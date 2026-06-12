---
title: "Thank you novation for your support!"
date: 2008-12-19
forum: Ubuntu Studio
---

### Post by barisurum on 2008-12-19
Hi everybody! This is not an advertisement. I post this here because I think it is important for us to know which hardware manufacturers support and care about the linux community.

   I recently posted emails to various audio interface manufacturers and got an answer from Novation. I asked novation music if I could use their x-station audio interface with linux. Here is the conversation between me and Andy Leung from Novation Support:

   
   Me:

   > Hello;

   I wonder if I can use x-station or any novation product with ubuntu studio linux distribution. I prefer linux because I can setup a DAW with less money with this software. Is support for this environment included?

   Novation:

   > Hi Baris,

Thanks for the email.

The X-station and Remote SL keyboards are class compliant device, therefore will work as a standard midi controller under Linux.

However the Automap Universal (which only supports the Remote SL range) software will not work under Linux.

Let me know if you need further info.

Best regards,

Andy Leung
Novation Support

   Me:

   > Hello and thanks for the reply;

   So I can use x-station as midi controller, can I use the audio interface too? And can I use standart sysex to transfer OS, patches etc. to the device? If these are true I will consider buying a unit.

   Thanks.

   Novation:

   > Hi Baris,

You need to update the X-station firmware to the latest version (3.0.03):

[http://www.novationmusic.com/support/software/xstation/](http://www.novationmusic.com/support/software/xstation/)

then both the audio and midi will be a combined device and work under linux, as they are now class compliant.

All the best,

Andy


   I bought my novation x-station today and upgraded the firmware (I had to use windows, because sysex editors won't work in wine for some reason) and guess what? Everything works perfectly! 
   I appreciated the help and wanted to share this experience with everybody. And I encourage everybody to take the same path when buying new stuff. Cheers! :guitar:

---

### Post by mortski on 2009-03-02
FYI you can upgrade the X-Station OS without Windows using amidi. It is as simple as:

```
amidi -p hw:1,0,0 -s XS3003\ OS.syx
```

where "hw:1,0,0" is the address listed when you run amidi -l and "XS3003\ OS.syx" is the OS upgrade sysex file. I can vouch for this technique as I've just updated my X-Station 25.

---

### Post by kokoshmusun on 2010-12-24
Wow this is great! So you plugin the X-Station and both the MIDI and the Audio interface works directly in Ubuntu?  How about the Novation Xio Synth?  I'm looking to acquire a USB audio/MIDI interface.

---

### Post by prokoudine on 2010-12-25
Yes, joint Focusrite/Novation team is quite friendly too. Perhaps I should go for a Novation keyboard after all :)

BTW it should be possible to receive/send SysEx on Linux even without console. Try talking to Christoph Eckert who does [Simple SysExxer]("http://www.christeck.de/wp/products/simple-sysexxer/").

---

### Post by sgx on 2010-12-26
Nice to know another company has a midi/audio compliant interface, and support staff treats you like a member of society. :)
Cheers

---

### Post by cchhrriiss121212 on 2010-12-26
Just thought I'd add my Novation Remote 49 works out of the box, all keys and sliders etc. are functional.

---

### Post by mango42 on 2010-12-29
:KS ++1

Focusrite & Novation couldn't be more helpful if they tried. Based on enquiries to them, I use a Novation zero SL without problems now and I'm fairly sure next time I try, the Saffire audio i/f will work too, with grateful thanks to the **ffado** team and their rapport with this company.

---

