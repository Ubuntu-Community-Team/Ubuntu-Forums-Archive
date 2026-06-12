---
title: "Midi drivers OSS vs. ALSA ?"
date: 2011-08-17
forum: Ubuntu Studio
---

### Post by JuanPabloCuervo on 2011-08-17
[http://www.innerclocksystems.com/New%20ICS%20Clock%20Watch.html](http://www.innerclocksystems.com/New%20ICS%20Clock%20Watch.html)
[IMG]http://www.innerclocksystems.com/Clock%20to%20Audio%202.jpg[/IMG]

---

### Post by JuanPabloCuervo on 2011-08-23
Windows Miditest4 32-Bits works with Wine... not all sysex messages but all other Midi.

RME hdsp9632 has no OSS drivers yet... could not test Oss vs. ALSA.
But Real WindowsXP sp2 vs. Linux+Wine YES!! TangoStudio1.1 64-Bit
P4 1.6Ghz vs. i7 920
same soundcard!
Tested Wine with different Emulations W7, Vista, XP, 95.
Linux is better...:D

Miditest 4.6 seems to work better with W7 Emulation.
[http://earthvegaconnection.com/evc/products/miditest/file/miditest49.zip](http://earthvegaconnection.com/evc/products/miditest/file/miditest49.zip)

Miditest 4.12 works better with 95 or Vista Emulation.

Next Test will be USB interfaces.

[http://earthvegaconnection.com/evc/products/miditest/#download](http://earthvegaconnection.com/evc/products/miditest/#download)
[SIZE=1]-------------------------------------------------------------------------- 
         MidiTest Results 
-------------------------------------------------------------------------- 



================ Info ==================================================== [/SIZE]      [SIZE=1]

Date:        23 Aug 2011 [/SIZE]  [SIZE=1]
Time:        01:52:21 
AppVersion:    4.12.252 
OS:        Microsoft Windows 95 
Processor(s):    Intel(R) Pentium(R) 4 CPU 2.40GHz 
Speed:        2668 MHz 
Number:        8 
API:        MultiMedia Extensions (MME) 
Test type:    Advanced 
Use timestamp:    yes 
Errors:        0 
Last error:    None 



================ Tested Message Types ==================================== [/SIZE]      [SIZE=1]

        Note off:                    yes [/SIZE]  [SIZE=1]
        Note on:                    yes 
        Key aftertouch:                    yes 
        Controller:                    yes 
        Program change:                    yes 
        Channel aftertouch:                yes 
        Pitchbend:                    yes 
        System exclusive:                    no 
        MIDI time code quarter frame:                no 
        Song position pointer:                    no 
        Song select:                        no 
        Tune request:                        no 
        MIDI clock:                        no 
        MIDI tick:                        no 
        Start:                        yes 
        Continue:                    yes 
        Stop:                        yes 
        Active sensing:                        no 
        System reset:                        no 
        System exclusive mixed with realtime messages:        no 



================ Ports =================================================== [/SIZE]      [SIZE=1]

MIDI Output:    Hammerfall DSP - HDSP MIDI 1 [/SIZE]  [SIZE=1]
Description:    Not available 
Provider:    Not available 
DriverDate:    Not available 
DriverVersion:    Not available 


MIDI Input:    Hammerfall DSP - HDSP MIDI 1 [/SIZE]    [SIZE=1]
Description:    Not available 
Provider:    Not available 
DriverDate:    Not available 
DriverVersion:    Not available 



================ Results Per Message ===================================== [/SIZE]      [SIZE=1]

MESSAGES           Snd           Rcv            Snd+Rcv [/SIZE]  [SIZE=1]

Message TotalTime:      262.93 ms    19778.69 ms    20041.62 ms [/SIZE]  [SIZE=1]
Message MaximumTime:        0.03 ms        1.65 ms        1.66 ms 
Message MinimumTime:        0.00 ms        0.00 ms        0.00 ms 
Message AverageTime:        0.01 ms        0.63 ms        0.64 ms 
SysexTime:            0.00 ms        0.00 ms        0.00 ms 
SysexAverage:            0.00 ms        0.00 ms        0.00 ms 

    <   1 ms:           31250       25781       25613 [/SIZE]  [SIZE=1]
  1 -   2 ms:               0        5469        5637 
  2 -   3 ms:               0           0           0 
  3 -   4 ms:               0           0           0 
  4 -   5 ms:               0           0           0 
  5 -  10 ms:               0           0           0 
 10 -  20 ms:               0           0           0 
 20 -  50 ms:               0           0           0 
 50 - 100 ms:               0           0           0 
    > 100 ms:               0           0           0 

Message count:           31250    Sysex count:           0 [/SIZE]  [SIZE=1]
Sysex size:               0    Sysex passed:           0 

Message latency:        0.64 ms    Total time:      50.995 sec [/SIZE]  [SIZE=1]
Message jitter:            0.38 ms 
Message max deviation:        1.01 ms 



================ Results Per Byte ======================================== [/SIZE]      [SIZE=1]

BYTES [/SIZE]  [SIZE=1]

Byte TotalTime:         7505.28 ms [/SIZE]  [SIZE=1]
Byte MaximumTime:        1.01 ms 
Byte MinimumTime:        0.00 ms 
Byte AverageTime:        0.24 ms 

    <   1 ms:           31249 [/SIZE]  [SIZE=1]
  1 -   2 ms:               1 
  2 -   3 ms:               0 
  3 -   4 ms:               0 
  4 -   5 ms:               0 
  5 -  10 ms:               0 
 10 -  20 ms:               0 
 20 -  50 ms:               0 
 50 - 100 ms:               0 
    > 100 ms:               0 

Byte count:           82369 [/SIZE]  [SIZE=1]

Byte latency:            0.24 ms [/SIZE]  [SIZE=1]
Byte jitter:            0.14 ms 
Byte max deviation:        0.77 ms[/SIZE]

---

