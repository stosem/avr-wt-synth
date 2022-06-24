# Info

Eurorack Wavetable-based VCO. Atari Glitch. DIY

# User manual

## Switch

* Random On/Off random feature.

If random feature is On, the new sound will be generated at each trigger CV signal

## Knobs

You can switch any knob to 0 value by turning it clockwise till the click.

| Parameter name | Description | Normal mode | Random mode |
| --- | --- | --- | --- |
| WAVE | WaveTable select | Select WaveTable from 0 to max available (MAX_WT) | Limit Random Wavetable. 0=ALL |
| OBER | Obertone freq | Set Obertone Freq | Limit Obertone Freq. 0=ALL |
| GLITCH | FM intensity | Set FM intensity | Limit FM intensity. 0=ALL |
| MOD | Modulation Rate | Set wah-wah effect | Limit Mod ratio. 0=ALL | 

## CVs

CVs have higher priority than knobs

| Parameter name | Description | Normal mode | Random mode |
| --- | --- | --- | --- |
| TRIG  | Trigger CV | Make a sound | Generate a random sound |
| V/OCT | Pitch CV | Set pitch (will be quantized to a note) | Set pitch. 0 or no signal = Random pitch |
| GLCH  | FM intensity | Set FM intensity | - |
| OBER  | Obertone freq | Set obertone freq | - |
| MOD   | Modulation Rate | Set wah-wah effect | - |

## Notes

Current range is 5 octaves from C1 to C6

## WaveTables

1. HSN - Half Sinus
2. SIN - Full Sinus
3. SQR - Square
4. SAW - Sawtooth
5. TRI - Triangle

# Developers

## Tips

* Do not use digital pins 11,12,13 if you want to use MOSI/MISO Atmega programmer (especially with capacitors)
* Do not use digital pins 9,10. They are used by Mozzi sound generator
* Change OpIntensityMod WaveTable if you want to get creazy sound
* Use DEBUG_INPUT to check CVs and knobs. But it's not a good idea to use the Serial messages with Mozzi. Don't forget to undefine debugs.

## Known bugs

* AutoMap doesn't work till it get the maximum value from CV/Knob. It returns always maximum.
We can't replace it with map() because it's very slow.
Fixed by pushing max value first.

* map() and AutoMap works not so good on the minimum value.
For example 0 and 15 - are the same values for it. Therefore C0 and C#0 - are the same notes.
Fixed by if-then-hack.
