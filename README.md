# Seven-segment-numbers-16x28
Reusable font with seven-segment numbers only, designed for Nokia 5110 display

## Usage with Arduino

Libraries needed
* [adafruit/Adafruit-PCD8544-Nokia-5110-LCD-library](//github.com/adafruit/Adafruit-PCD8544-Nokia-5110-LCD-library)
* [adafruit/Adafruit-GFX-Library](//github.com/adafruit/Adafruit-GFX-Library)

```cpp
//positions on 84 pixel width display
//16+4+16+4+4+4+16+4+16 = 84

void printHour() {
  int local=hour();
  if (local / 10 > 0) {
    display.drawBitmap(0,0,lcd[local / 10],16,28,BLACK);
  }
  display.drawBitmap(20,0,lcd[local % 10],16,28,BLACK);
}

void printDelimiter() {
  display.fillRect(40,7,4,4,BLACK);
  display.fillRect(40,15,4,4,BLACK);
}

void printMinute() {
  int local=minute();
  display.drawBitmap(48,0,lcd[local / 10],16,28,BLACK);
  display.drawBitmap(68,0,lcd[local % 10],16,28,BLACK);
}
```

Complete drawing may looks like
```cpp
  display.clearDisplay();
  printHour();
  printMinute();
  if (second()%2 == 0) {
    printDelimiter();
  }
display.display();
```
