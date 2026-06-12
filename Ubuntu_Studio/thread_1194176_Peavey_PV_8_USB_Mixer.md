---
title: "Peavey PV 8 USB Mixer"
date: 2009-06-22
forum: Ubuntu Studio
---

### Post by k1773r37f on 2009-06-22
Howdy fellow Ubunters,

I am considering the purchase of a Peavey PV 8 USB mixer. It comes highly recommended by a musician buddy of mine. However he is not a Linux user. I need this as part of a mobile recording/live studio for my daughter. Does anybody have experience with this or any USB mixers under Linux? I need at least 4 mic/instrument channels and at least two (left/right) stereo line in channels. As well as head phones/monitors and Mains out.  Also, since I will be recording to my Ubuntu Laptop,  I will need to be able to record audio captured through the USB port.

Thanx,

The Killer Elf

---

### Post by sgx on 2009-06-22
if your google search finds no linux hits, but it works OK with a Mac, find one at a shop and plug it in to your laptop. Install usbview ahead of time, wine/wineasio/reaper might also be good for testing, and see whats shakin in the details :)

---

### Post by k1773r37f on 2009-07-01
I went out on a limb and purchased it.  With minor fiddling with in the Audacity app I was able to record a clean audio sample using 3 of the channels.  

All of the mixing has to be done on the board, wich is ok.  It presents  a single mono or two stereo channels to Audacity.  Which is fine.  

Although, all 8 channels are being presented to the USB subsystem as separate PCM devices. 




Perhaps I will fiddle with JACK and see if there is away to deal with each of the  eight channels separately.  If so,  I'll report back here.  But sofar, I am pleased.  

The mains are a little noisy when the USB is plugged in.  But the captured sound is clean.  I do have to make the mike a little hotter than usual.  But if I turn down the amps volume I can control the feed back ok.

My prerecorded music levels are easy to control.  That is what I was after, being able to control recorded music for a live singer and mix it all and capture the mix onto my laptop.

One thing I did note.  You should uncheck everything in the Playthrough section in the Audacity Audio IO section or you will get terrible dropouts somtimes 1/4 second or more.  This maybe par for the course for recording thru USB devices.  This is the first time I have tried it.  But unchecking these does totally aleviate the problem and the captured sound is clean.  

Thanx  and I will report back any new findings I have.  Especailly if I manage to get each of the 8 channels to show up in Jack or Audacity.

---

### Post by trulan on 2009-07-02
If you can get it to sync with Jack, I would definitely look into using Ardour for recording rather than Audacity.  It is directed much more towards handling multiple channels, whereas Audacity's thing is destructive audio editing.  But you'll need to have Jack up and running for Ardour to work.

---

### Post by k1773r37f on 2010-02-04
I got this board working beautifully with alsa and jackd.  On my desk top machine with a rt kernel, I do not even experience drop outs.  with jack I am able to break out each of the mixing channels and  assign different effects to them. The sound from the mains is clean too. I am really happy with this setup. Once I am finished tweaking, I will post my asound.conf here. 

Thanx,
Kill3r37f

---

### Post by robeast on 2010-02-04
Awesome work k1773r37f! Thanks for going out on a limb and trying this out. That looks like a very capable mixer, glad to hear it is working well with Linux. Can you give us some more specifics about your computer hardware, Ubuntu version, etc?

---

### Post by k1773r37f on 2010-02-05
Lappy is a Compaq Persario V5000 AMD Turon 64 running Ubuntu Karmic vanilla 64bit 2.6.32(?) kernel.  1 GB Ram.   (Room temperature right now.  Can't login to get actual kernel version,  relying on synaptically challenged memory)

Desktop is a home grown AMD Athalon 2.8 Ghz with 2 GB ram Ubuntu Hardy running a Real time Low latency 2.6.24-21 32 bit kernel. (posting from this machine)  

The Lappy and the Peavey are my mobile studio.  The desktop with the same Peavey 8 USB is my home studio. This is the one that I have modified the most to get the Peavey working most optimaly.  

This machine also has an on board VIA Surround sound system.  Unfortunately. tonights expiermentation lost the 8 separate channels I had access to from the Peavey.  Now I am only seeing the two again.  But I am sure I can get it back.   

I did not have sound processing/production/engineering in mind when purchasing/building either of these machines.  They are just what I happen to have on hand.  The desktop is working out really well.  

The lappy barely gets by.  I thought having a 64 bit processor and kernel would be really great.  But the lil ol' 32 bit Athalon is out performing the 64 bit Turion under the table.  Go figure.  Granted,  I haven't done the work on the Lappy's  kernel that I have done on the desktop.  But the desktop started out performing better even before the kernel enhancements.

Not really relevant to this discussion.  The lappy has a ATI Express 200M graphics card 128 MB Shared RAM (yuck).  The Desktop has an Nvidia Gforce 4 graphics card. 64 MB dedicated RAM.

Well,  gotta give the neurons a break. I probably won't get a chance to play again until next weekend.  Then  I'll work out how to get the separate channels again. Gotta focus on day job  and how to mirror an existing disk with LVM volumes on it.
Can't just reload.  It's a production machine.  should have been mirrored in the beginning.  Oh well.  Now I am rambling.  I get that way when tired.

---

### Post by k1773r37f on 2010-02-10
Ok I have been pursuing feral water foul.  I never really had the 8 channels presented thru the USB to the alsa sound subsystem.  I think I just had a bunch o' Jack Rack channels and thought these were coming from the sound board. 

According to Peavey this board just presents the mixed main out to the USB System.  I  still can't quite grokk this lsusb -v -d 08bb:2901 out put though.

Bus 001 Device 003: ID 08bb:2901 Texas Instruments Japan 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x08bb Texas Instruments Japan
  idProduct          0x2901 
  bcdDevice            1.00
  iManufacturer           1 Burr-Brown from TI              
  iProduct                2 USB Audio CODEC 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength         1191
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      1 Control Device
      bInterfaceProtocol      0 
      iInterface              0 
      AudioControl Interface Descriptor:
        bLength                10
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdADC               1.00
        wTotalLength           62
        bInCollection           2
        baInterfaceNr( 0)       1
        baInterfaceNr( 1)       2
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bNrChannels             2
        wChannelConfig     0x0003
          Left Front (L)
          Right Front (R)
        iChannelNames           0 
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             2
        wTerminalType      0x0301 Speaker
        bAssocTerminal          0
        bSourceID               3
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                10
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                 3
        bSourceID               1
        bControlSize            1
        bmaControls( 0)      0x01
          Mute
        bmaControls( 1)      0x02
          Volume
        bmaControls( 2)      0x02
          Volume
        iFeature                0 
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             4
        wTerminalType      0x0201 Microphone
        bAssocTerminal          0
        bNrChannels             2
        wChannelConfig     0x0003
          Left Front (L)
          Right Front (R)
        iChannelNames           0 
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             5
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID               4
        iTerminal               0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           1
        bDelay                  0 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                17
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             2
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            3 Discrete
        tSamFreq[ 0]        32000
        tSamFreq[ 1]        44100
        tSamFreq[ 2]        48000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            9
          Transfer Type            Isochronous
          Synch Type               Adaptive
          Usage Type               Data
        wMaxPacketSize     0x00c0  1x 192 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay            512 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           1
        bDelay                  0 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                17
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            3 Discrete
        tSamFreq[ 0]        32000
        tSamFreq[ 1]        44100
        tSamFreq[ 2]        48000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            9
          Transfer Type            Isochronous
          Synch Type               Adaptive
          Usage Type               Data
        wMaxPacketSize     0x0060  1x 96 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay            512 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           1
        bDelay                  0 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                17
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             2
        bSubframeSize           1
        bBitResolution          8
        bSamFreqType            3 Discrete
        tSamFreq[ 0]        32000
        tSamFreq[ 1]        44100
        tSamFreq[ 2]        48000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            9
          Transfer Type            Isochronous
          Synch Type               Adaptive
          Usage Type               Data
        wMaxPacketSize     0x0060  1x 96 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay            512 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           1
        bDelay                  0 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                17
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           1
        bBitResolution          8
        bSamFreqType            3 Discrete
        tSamFreq[ 0]        32000
        tSamFreq[ 1]        44100
        tSamFreq[ 2]        48000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            9
          Transfer Type            Isochronous
          Synch Type               Adaptive
          Usage Type               Data
        wMaxPacketSize     0x0030  1x 48 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay            512 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           1
        bDelay                  0 frames
        wFormatTag              2 PCM8
      AudioStreaming Interface Descriptor:
        bLength                17
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             2
        bSubframeSize           1
        bBitResolution          8
        bSamFreqType            3 Discrete
        tSamFreq[ 0]        32000
        tSamFreq[ 1]        44100
        tSamFreq[ 2]        48000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            9
          Transfer Type            Isochronous
          Synch Type               Adaptive
          Usage Type               Data
        wMaxPacketSize     0x0060  1x 96 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay            512 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       6
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           1
        bDelay                  0 frames
        wFormatTag              2 PCM8
      AudioStreaming Interface Descriptor:
        bLength                17
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           1
        bBitResolution          8
        bSamFreqType            3 Discrete
        tSamFreq[ 0]        32000
        tSamFreq[ 1]        44100
        tSamFreq[ 2]        48000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            9
          Transfer Type            Isochronous
          Synch Type               Adaptive
          Usage Type               Data
        wMaxPacketSize     0x0030  1x 48 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay            512 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           5
        bDelay                  0 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             2
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        48000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x00c4  1x 196 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay              0 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       2
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           5
        bDelay                  0 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        48000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0062  1x 98 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay              0 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       3
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           5
        bDelay                  0 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             2
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        44100
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x00b4  1x 180 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay              0 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       4
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           5
        bDelay                  0 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        44100
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x005a  1x 90 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay              0 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       5
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           5
        bDelay                  0 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             2
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        32000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0084  1x 132 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay              0 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       6
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           5
        bDelay                  0 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        32000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0042  1x 66 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay              0 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       7
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           5
        bDelay                  0 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             2
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        22050
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x005c  1x 92 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay              0 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       8
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           5
        bDelay                  0 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        22050
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x002e  1x 46 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay              0 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       9
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           5
        bDelay                  0 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             2
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        16000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0044  1x 68 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay              0 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting      10
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           5
        bDelay                  0 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        16000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0022  1x 34 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay              0 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting      11
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           5
        bDelay                  0 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             2
        bSubframeSize           1
        bBitResolution          8
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        16000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0022  1x 34 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay              0 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting      12
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           5
        bDelay                  0 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           1
        bBitResolution          8
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        16000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay              0 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting      13
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           5
        bDelay                  0 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             2
        bSubframeSize           1
        bBitResolution          8
        bSamFreqType            1 Discrete
        tSamFreq[ 0]         8000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0012  1x 18 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay              0 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting      14
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           5
        bDelay                  0 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           1
        bBitResolution          8
        bSamFreqType            1 Discrete
        tSamFreq[ 0]         8000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay              0 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting      15
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           5
        bDelay                  0 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             2
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        11025
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes           13
          Transfer Type            Isochronous
          Synch Type               Synchronous
          Usage Type               Data
        wMaxPacketSize     0x0030  1x 48 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay              0 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting      16
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           5
        bDelay                  0 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        11025
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes           13
          Transfer Type            Isochronous
          Synch Type               Synchronous
          Usage Type               Data
        wMaxPacketSize     0x0018  1x 24 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay              0 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting      17
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           5
        bDelay                  0 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             2
        bSubframeSize           1
        bBitResolution          8
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        11025
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes           13
          Transfer Type            Isochronous
          Synch Type               Synchronous
          Usage Type               Data
        wMaxPacketSize     0x0018  1x 24 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay              0 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting      18
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           5
        bDelay                  0 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           1
        bBitResolution          8
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        11025
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes           13
          Transfer Type            Isochronous
          Synch Type               Synchronous
          Usage Type               Data
        wMaxPacketSize     0x000c  1x 12 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay              0 Decoded PCM samples
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      31
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              10
Device Status:     0x0001
  Self Powered

It looks like there are a lot of goodies there just waiting to be hacked!



Here is my .asoundrc.  But I think this is redundant.  I don't think one really needs it.



pcm.!default {
type dmix
card default
}
ctl.!default {
type dmix
card default
}

Anyway's this little gizmo is working as designed. And for what it is I am happy. It is serving the purpose for which I purchased it well.  

I just thought it would be neat to grab the individual channels process those and return the processed sound to the mains.  Maybe make my daughter sound like a Chippet on a couple of songs.

We can say this one works with Linux!

Best Regards,
Killer Elf

---

### Post by k1773r37f on 2010-02-10
The formatting of my lsusb output was lost in traslation.  I'll attach it as a file incase someone feels like hacking. It is an Open Document format file.

---

### Post by k1773r37f on 2010-02-11
I don't think I am gonna give up yet.  This is what usbview shows.  I might loos formatting.  So please bear with me.
[HTML]
<code>
USB Audio CODEC 
Manufacturer: Burr-Brown from TI              
Speed: 12Mb/s (full)
USB Version:  1.10
Device Class: 00(>ifc )
Device Subclass: 00
Device Protocol: 00
Maximum Default Endpoint Size: 8
Number of Configurations: 1
Vendor Id: 08bb
Product Id: 2901
Revision Number:  1.00

Config Number: 1
	Number of Interfaces: 4
	Attributes: c0
	MaxPower Needed:   0mA

	Interface Number: 0
		Name: snd-usb-audio
		Alternate Number: 0
		Class: 01(audio) 
		Sub Class: 01
		Protocol: 00
		Number of Endpoints: 0

	Interface Number: 1
		Name: snd-usb-audio
		Alternate Number: 0
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 0

	Interface Number: 1
		Name: snd-usb-audio
		Alternate Number: 1
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 02
			Direction: out
			Attribute: 9
			Type: Isoc
			Max Packet Size: 192
			Interval: 1ms

	Interface Number: 1
		Name: snd-usb-audio
		Alternate Number: 2
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 02
			Direction: out
			Attribute: 9
			Type: Isoc
			Max Packet Size: 96
			Interval: 1ms

	Interface Number: 1
		Name: snd-usb-audio
		Alternate Number: 3
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 02
			Direction: out
			Attribute: 9
			Type: Isoc
			Max Packet Size: 96
			Interval: 1ms

	Interface Number: 1
		Name: snd-usb-audio
		Alternate Number: 4
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 02
			Direction: out
			Attribute: 9
			Type: Isoc
			Max Packet Size: 48
			Interval: 1ms

	Interface Number: 1
		Name: snd-usb-audio
		Alternate Number: 5
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 02
			Direction: out
			Attribute: 9
			Type: Isoc
			Max Packet Size: 96
			Interval: 1ms

	Interface Number: 1
		Name: snd-usb-audio
		Alternate Number: 6
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 02
			Direction: out
			Attribute: 9
			Type: Isoc
			Max Packet Size: 48
			Interval: 1ms

	Interface Number: 2
		Name: snd-usb-audio
		Alternate Number: 0
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 0

	Interface Number: 2
		Name: snd-usb-audio
		Alternate Number: 1
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 84
			Direction: in
			Attribute: 5
			Type: Isoc
			Max Packet Size: 196
			Interval: 1ms

	Interface Number: 2
		Name: snd-usb-audio
		Alternate Number: 2
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 84
			Direction: in
			Attribute: 5
			Type: Isoc
			Max Packet Size: 98
			Interval: 1ms

	Interface Number: 2
		Name: snd-usb-audio
		Alternate Number: 3
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 84
			Direction: in
			Attribute: 5
			Type: Isoc
			Max Packet Size: 180
			Interval: 1ms

	Interface Number: 2
		Name: snd-usb-audio
		Alternate Number: 4
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 84
			Direction: in
			Attribute: 5
			Type: Isoc
			Max Packet Size: 90
			Interval: 1ms

	Interface Number: 2
		Name: snd-usb-audio
		Alternate Number: 5
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 84
			Direction: in
			Attribute: 5
			Type: Isoc
			Max Packet Size: 132
			Interval: 1ms

	Interface Number: 2
		Name: snd-usb-audio
		Alternate Number: 6
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 84
			Direction: in
			Attribute: 5
			Type: Isoc
			Max Packet Size: 66
			Interval: 1ms

	Interface Number: 2
		Name: snd-usb-audio
		Alternate Number: 7
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 84
			Direction: in
			Attribute: 5
			Type: Isoc
			Max Packet Size: 92
			Interval: 1ms

	Interface Number: 2
		Name: snd-usb-audio
		Alternate Number: 8
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 84
			Direction: in
			Attribute: 5
			Type: Isoc
			Max Packet Size: 46
			Interval: 1ms

	Interface Number: 2
		Name: snd-usb-audio
		Alternate Number: 9
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 84
			Direction: in
			Attribute: 5
			Type: Isoc
			Max Packet Size: 68
			Interval: 1ms

	Interface Number: 2
		Name: snd-usb-audio
		Alternate Number: 10
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 84
			Direction: in
			Attribute: 5
			Type: Isoc
			Max Packet Size: 34
			Interval: 1ms

	Interface Number: 2
		Name: snd-usb-audio
		Alternate Number: 11
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 84
			Direction: in
			Attribute: 5
			Type: Isoc
			Max Packet Size: 34
			Interval: 1ms

	Interface Number: 2
		Name: snd-usb-audio
		Alternate Number: 12
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 84
			Direction: in
			Attribute: 5
			Type: Isoc
			Max Packet Size: 17
			Interval: 1ms

	Interface Number: 2
		Name: snd-usb-audio
		Alternate Number: 13
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 84
			Direction: in
			Attribute: 5
			Type: Isoc
			Max Packet Size: 18
			Interval: 1ms

	Interface Number: 2
		Name: snd-usb-audio
		Alternate Number: 14
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 84
			Direction: in
			Attribute: 5
			Type: Isoc
			Max Packet Size: 9
			Interval: 1ms

	Interface Number: 2
		Name: snd-usb-audio
		Alternate Number: 15
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 84
			Direction: in
			Attribute: 13
			Type: Isoc
			Max Packet Size: 48
			Interval: 1ms

	Interface Number: 2
		Name: snd-usb-audio
		Alternate Number: 16
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 84
			Direction: in
			Attribute: 13
			Type: Isoc
			Max Packet Size: 24
			Interval: 1ms

	Interface Number: 2
		Name: snd-usb-audio
		Alternate Number: 17
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 84
			Direction: in
			Attribute: 13
			Type: Isoc
			Max Packet Size: 24
			Interval: 1ms

	Interface Number: 2
		Name: snd-usb-audio
		Alternate Number: 18
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 84
			Direction: in
			Attribute: 13
			Type: Isoc
			Max Packet Size: 12
			Interval: 1ms

	Interface Number: 3
		Name: usbhid
		Alternate Number: 0
		Class: 03(HID  ) 
		Sub Class: 00
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 85
			Direction: in
			Attribute: 3
			Type: Int.
			Max Packet Size: 1
</code>			Interval: 10ms
[/HTML]
Dang it.  I still say I ought to be able to grab these thru alsa/jack. Peavey probably didn't intend it. And only the two channels show up on the Windows laptop I use for work.  I coulda swore I had it at one time.  I shoulda left well enough alone.

Gotta turn in now.  But I will keep hackin'

---

### Post by sheehanje on 2010-02-11
The first thing I noticed is you are connected USB 1.1.  Is that because of the device, or because of the USB port on the computer?  I'm not an expert with this, but I don't think USB 1.1 would cleanly handle 8 channels at once.

I looked up the specs of the Peavey PV8 on Sweetwater, and it says the USB can handle either the main outs or the tape out, which leads me to believe you can't record 8 channels separately.  Rather the 8 Channels will get mixed to 2.  I've seen this with other Mixers with USB connectivity.  If this is the case, it won't matter if you use Linux or Windows.

Like I said, I'm not an expert with this stuff, but I have run across similar mixers that only support 2 channels out through USB.

---

### Post by AutoStatic on 2010-02-11
> **sheehanje said:**
> The first thing I noticed is you are connected USB 1.1.  Is that because of the device, or because of the USB port on the computer?  I'm not an expert with this, but I don't think USB 1.1 would cleanly handle 8 channels at once.The device is USB1.1 so due to the limited bandwidth you just cannot use more than two channels at once afaik. If you want more channels you either need a USB2 or Firewire device.

---

### Post by liberty_nz on 2010-03-05
So is there any USB 2.0 mixers out there that work with ubuntu? 
I'm keen to set up some home recording with my eee.

---

### Post by Capoeira on 2010-03-05
> **liberty_nz said:**
> So is there any USB 2.0 mixers out there that work with ubuntu? 
I'm keen to set up some home recording with my eee.

[http://www.linuxjournal.com/article/10240](http://www.linuxjournal.com/article/10240)

---

### Post by Jeremylc on 2010-05-21
> **Capoeira said:**
> [http://www.linuxjournal.com/article/10240](http://www.linuxjournal.com/article/10240)

Unfortunately, that is a MIDI controller, not an audio mixer.

---

### Post by Capoeira on 2010-05-21
> **Jeremylc said:**
> Unfortunately, that is a MIDI controller, not an audio mixer.

i did'nt understand....in the box mixing you do with MIDI

---

### Post by k1773r37f on 2010-05-23
> **liberty_nz said:**
> So is there any USB 2.0 mixers out there that work with ubuntu? 
I'm keen to set up some home recording with my eee.

The PV USB 8 is a USB 2.0 mixer.  However, the ancient machine I had it conneccted to at the time only had USB 1.0 ports available. BTW,  I have an eee pc.  I don't think it is up to the task of sound processing of this magnitude. I'd look into a more full function lappy running Ubuntu Studio.

---

### Post by Jeremylc on 2010-05-25
> **k1773r37f said:**
> The PV USB 8 is a USB 2.0 mixer.  However, the ancient machine I had it conneccted to at the time only had USB 1.0 ports available. BTW,  I have an eee pc.  I don't think it is up to the task of sound processing of this magnitude. I'd look into a more full function lappy running Ubuntu Studio.

So, does that mean the individual channels may actually be accessible? (My EEE PC may not have the horsepower, but my MBP surely does :) )

---

### Post by JC Cheloven on 2010-05-25
> **liberty_nz said:**
> So is there any USB 2.0 mixers out there that work with ubuntu? 
I'm keen to set up some home recording with my eee.
Unfortunately, usb2.0 lacks a standard, so it's diffucult for linux audio developpers to make those devices to work. Some of them are reported to work, many of them with issues. For example I've heard this one records ok in all channels, but has problems at playback.
[http://www.roland.com/products/en/M-16DX/index.html](http://www.roland.com/products/en/M-16DX/index.html)

---

### Post by k1773r37f on 2010-05-27
> **Jeremylc said:**
> So, does that mean the individual channels may actually be accessible? (My EEE PC may not have the horsepower, but my MBP surely does :) )

Sorry, only the mains are actually presented to the USB.  When I thought I had all channels, I had in fact only setup different jack channels to the same two channels.  I was still learning jack at the time as well.  I am rather new to all this computer sound engineering stuff.

Thanx,
Killer Elf

---

### Post by adel.wahba on 2010-05-28
[[COLOR=#444444]http://www.linuxjournal.com/article/10240[/COLOR]]("http://www.linuxjournal.com/article/10240")

---

### Post by adel.wahba on 2010-05-28
understand....in the box mixing you do with MIDI

---

### Post by iangreentree on 2011-11-17
Hi All, my very first Post.

I have aquired a PV10 USB mixer to use with Ubuntu Studio.  I can say it works great and was picked up by JACK with out too much fiddling about.  I can confirm that the mixer only outputs the 2 master channel via USB as I had a look through the [owner manual]("http://www.peavey.com/products/proaudio/mixers/pv/index.cfm/item/116340/PV%26nbsp%3B10%26nbsp%3BUSB.html") and found the wiring diagram.  The USB output is taken from Master/Headphone signal.  Checking the owners manuals for PV6 USB and PV8 USB, it looks like this is standard for all Peavey PV USB mixer models.

The Tape to Control and the Tape to Mix switches also managed the USB signal on the mixer.

Hope this helps anyone visiting this Thread as this mixer is a great addition to my Ubuntu Studio.

---

