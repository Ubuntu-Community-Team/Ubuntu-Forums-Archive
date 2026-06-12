---
title: "Wine + EnergyXT + WineASIO + Jack"
date: 2009-12-27
forum: Ubuntu Studio
---

### Post by mikep_bluefish on 2009-12-27
I'm posting this thread for anyone who might be interested in running the WindoZe version of Energy XT on Ubuntu (because in the Linux version you can't load those damn DLL plugins.. :-x )

The amazing thing about it is that you can also use the WindoZe Energy XT version in Jack's Connections window the same way you can with the Linux version!! :shock:

I have attachments of the files that I've used and a screenshot of [Win] eXT connected to [Lin] Audacity that proves how amazing the Jack Server is :!::!::!:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=141366&stc=1&d=1261940411[/IMG]
  

0. INSTALL WINE & JACK AUDIO SERVER AND SET WINE's AUDIO TO JACK

1. COPY 'energyXT' IN THE 'opt/' DIRECTORY

2. COPY 'MSVCP60.DLL' in the '/opt/energyXT/' DIRECTORY

3. EXTRACT 'wineasioinstaller-0.7.4-2.tar.gz' SOMEWHERE AND RUN THE 'wineasioinstaller-0.7.4-2' SCRIPT TO INSTALL ASIO SUPPORT FOR WINE.

4. YOU MIGHT ALSO NEED TO OPEN A TERMINAL AND RUN THE COMMAND 'regsvr32 wineasio.dll' TO REGISTER THE WINE ASIO. 

5. START JACK

6. RUN '/opt/energyXT/energyXT.exe



P.S. Both WindoZe and Linux EnergyXT can also work without Jack...

---

### Post by thomasjw on 2010-01-17
i wish i could duplicate your results (because i loved energyxt back before my windows died), but so far i've been unsuccessful.  when energyxt starts i'm unable to choose 'asio' in its audio setup dialog, and when i try the command 'regsvr32 wineasio.dll' i always get 'Failed to load wineasio.dll.'  (no explanation or further information, just 'failed to load.')  I also can't get energyxt to make any sound, or get its transport to move when i try to play the demo track.

i've configured wine to use jack, the test sound works as expected.
jack server starts with no problems.  
i've got energyxt in the directory you specify, with the MSVCP60.DLL copied to the same directory.  
i ran the wineasio install script, got no errors.  

i don't even know where to look to find the problem...

---

### Post by thomasjw on 2010-01-18
i found the problem!  what i needed to know, and your otherwise-helpful walkthru doesn't specify, is that in order for the command 'regsvr32 wineasio.dll' to succeed, the file wineasio.dll.so must be copied/moved to the directory /usr/lib/wine/ (which is full of other .dlls).
  
once it was there, regsvr32 successfully registered wineasio, and then when i launched jack & eXT everything worked like magic.  now running energyxt with windows vsts in ubuntu... best thing ever!

---

### Post by PC_load_letter on 2010-06-02
I'm having troubles w/ the latest wineasio + energyxt 2.5.2 in Karmic 64bit. When I ran reg32 wineasio.dll, I got a "registered successfully" message.

Setting up Wine to use the ASIO driver seems to be the only way that makes enegyxt see my soundcard, an m-audio 2496.
This way I can play the demo song/project that comes with energyxt no problem, set up the audio options no problem, but...
I **CAN'T** choose the m-audio as my MIDI-in!!!?? It shows up as an option but when I click on it a check mark appears and disappears a millisecond later ](*,)](*,)](*,)

Anyone has a clue how to fix this? 

**P.S.** I tried the instructions given by the OP, but in that case XT does not see any midi devices.

---

### Post by sgx on 2010-06-02
> **PC_load_letter said:**
> I'm having troubles w/ the latest wineasio + energyxt 2.5.2 in Karmic 64bit. When I ran reg32 wineasio.dll, I got a "registered successfully" message.

Setting up Wine to use the ASIO driver seems to be the only way that makes enegyxt see my soundcard, an m-audio 2496.
This way I can play the demo song/project that comes with energyxt no problem, set up the audio options no problem, but...
I **CAN'T** choose the m-audio as my MIDI-in!!!?? It shows up as an option but when I click on it a check mark appears and disappears a millisecond later ](*,)](*,)](*,)

Anyone has a clue how to fix this? 

**P.S.** I tried the instructions given by the OP, but in that case XT does not see any midi devices.

I have a revision 2 maudio 2496 (check the output from  lspci  for yours

On the qjackctl setup page, choose 'none' for midi device.
run winecfg  and in the audio section, choose only alsa.

back at the qjackctl setup page

Input device  >
Output device  >

click the > widgets and select the ICE1712 multi

I also blacklisted the motherboard soundchip,
since apps defaulting to various sound engines switched the
audio output without asking.

/etc/modprobe.d/blacklist   The textfile is simply

blacklist snd-usb-audio
blacklist snd_intel8x0

Cheers

---

### Post by PC_load_letter on 2010-06-02
Fixed! That was AWESOME. Thank you sgx, I really appreciate it. I didn't have to blacklist my onboard device though, but I'm thinking that I may have disabled it from the BIOS, not sure though, it was a couple of years ago.
I couldn't find any other sound device from the output of lspci.

Thanks again!

---

### Post by sgx on 2010-06-03
My pleasure, glad its working, us earthlings needs more music :)

---

### Post by mango42 on 2010-06-08
Agreed! More music, less jingoism!

Maybe I should give EnergyXT a try as I'm bogged down getting Reaper to work - perhaps someone could clarify a very fundamental block I have - should I be able to run Reaper (x64) via WINE on an amd64 version of Lucid Studio - that is, in 64bit mode? The only response I'm getting from WINE is a tiny error message with corrupt characters followed by an error message telling me I'm not running 64bit Windows XP...

---

### Post by starrchildd on 2010-07-02
> **thomasjw said:**
> i wish i could duplicate your results (because i loved energyxt back before my windows died), but so far i've been unsuccessful.  when energyxt starts i'm unable to choose 'asio' in its audio setup dialog, and when i try the command 'regsvr32 wineasio.dll' i always get 'Failed to load wineasio.dll.'  (no explanation or further information, just 'failed to load.')  I also can't get energyxt to make any sound, or get its transport to move when i try to play the demo track.

i've configured wine to use jack, the test sound works as expected.
jack server starts with no problems.  
i've got energyxt in the directory you specify, with the MSVCP60.DLL copied to the same directory.  
i ran the wineasio install script, got no errors.  

i don't even know where to look to find the problem...
when you try to register wineasio and it fails all you have to do is reinstall it then register it again and it should work

---

