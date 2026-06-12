---
title: "Audacity BAD or My Sound Card ??"
date: 2010-08-02
forum: Ubuntu Studio
---

### Post by jmfal on 2010-08-02
Trying to record using audacity,just trying to transfer my vinyl to cd.

 I got it to record something once, won`t do it anymore.

I have playback, sounds good using guaeyadeque. Tried rt, lowlatency, and 

generic kernel. got it to record on lowlatency. 

 I think there may be a problem with my sound card. I tried some commands from some stickies and other threads:

aplay-l   hda nvidia alc1200

lspci -v  nvidia corp mcp61
          kernel driver in use:hda intel
          kernal modules: snd-hda-intel

sudo modprobe snd-  reply:fatal: module snd-  not found
  I`m not sure this is a complete command?

sudo dmidecode -t baseboard    reply: realtek hd audio codec alc888s

cat/proc/asound/card0/codec#* | grep codec         reply: realtek alc1200

I`m confused alc1200 or alc888s??

do i need to set user/permissions for audacity or my sound card or both?

Sort of new to ubuntu, not scared of the terminal, don`t know all the commands.

I`m guessing that the codecs aren`t being loaded, or this sound card isn`t any good for recording or audacity is broke.

10.04 64bit Learning how to find/ edit files so be patient with me!

Athlon IIx2 2.7  6gbsddr2 nvidia9100 maxtor160gbs

any/all help is greatly appreciated.

---

