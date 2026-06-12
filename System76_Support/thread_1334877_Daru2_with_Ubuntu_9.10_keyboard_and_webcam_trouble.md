---
title: "Daru2 with Ubuntu 9.10: keyboard and webcam trouble"
date: 2009-11-22
forum: System76 Support
---

### Post by Mr. Farlops on 2009-11-22
Recently I backed up my data and, on a clean disk, installed 9.10 on my Daru2 laptop. I followed the procedures outlined in the System76 knowledgebase:

[LIST=1]
[*]From a 9.10 install disk I installed the system. 
[*]Eeverything went fine but my keyboard is not quite properly recognized and this lead to some dead keys.
[*]Additionally, pressing the P2 switch doesn't turn on the built in webcam as it should. I don't see it listed after the lsusb command before or after hitting the P2 switch.
[*]Pressing the P2 switch instead launches a "Search for Files" dialog.
[*]Undaunted, I install all the latest updates via the Update Manager.
[*]Lastly I install the System76 driver and take the restore option.
[/LIST]

The problems persist. Pressing the P2 doesn't change the output of the lsusb command. I never see this:

```
Bus 007 Device 006: ID 0c45:62c0 Microdia
```

Which is the way the webcam should identify itself to linux. 

Pressing the P2 switch still launches the search for files dialog and the ALT GR key is still dead on my keyboard. Perhaps the two problems are related? Maybe in failing to recognize my keyboard layout, Ubuntu has misassigned the P2 switch and thus won't turn the webcam circuits on to be recognized?

I've looked through a couple of other threads here describing similar problems to mine but none of these suggestions seem to help. Any suggestions would be appreciated. I also realize that Daru2s are no longer being sold and thus may not be viable for any support.

---

### Post by imhavoc on 2009-11-23
I'm getting the same behavior with P2, but my Alt Gr key is working fine.

---

### Post by thomasaaron on 2009-11-23
We've seen that P2 problem twice before. On one occasion, re-imgaging fixed it. On the other occasion, it was a hardware issue.

Are you sure it was working in 9.04? Please boot from a 9.04 CD to see if it works. Then boot from a 9.10 CD to see if it works.

Go to System > Prefs > Keyboard > Layout and verify that you are using "Generic 105-key (Intl)" and "U.S." for your layout.

Also, are either of you dual-booting Windows?

---

### Post by tuebinger on 2009-11-23
Hello. I have a daru2 (ms 1221) and I'm having a similar problem with my webcam not working. I did a clean install of 64-bit 9.10 but I still can't turn on the webcam with the P2 button.  All the P2 button does is open the file finder.

In answer to the question above, yes, I have had Windows Vista installed on my computer.  Did that cause the problem with the webcam?

Thank you in advance for any advise you can give!

---

### Post by Mr. Farlops on 2009-11-24
> **thomasaaron said:**
> Are you sure it was working in 9.04?

Well, it was working in 8.04 LTS. But then, on a whim, I decided to upgrade to 9.10.

> **thomasaaron said:**
> Please boot from a 9.04 CD to see if it works. Then boot from a 9.10 CD to see if it works.

Should I boot from a live 8.04 CD and then a 9.10 CD given my answer above? I'll find or make an 8.04 live CD but I'll test with the 9.10 live and report here what I find.

> **thomasaaron said:**
> Go to System > Prefs > Keyboard > Layout and verify that you are using "Generic 105-key (Intl)" and "U.S." for your layout.

I did that but my ALT GR key still doesn't seem to be working as an ALT key. I know that internationally, the ALT GR is not quite the same as a US right ALT key. Is there something I'm overlooking here? The flag key doesn't seem to work the same way it used to either. In older versions of Ubuntu it opened the applications menu on the top panel. 

Otherwise all the other keys work just as they should. It's not  a major pain, I'm just curious what to expect. 


> **thomasaaron said:**
> Also, are either of you dual-booting Windows?

Nope. Never did.

---

### Post by thomasaaron on 2009-11-24
Mr Farlops,

Yes. Boot into the last version of Ubuntu in which you remembered it working so that we can determine if it is an Ubuntu issue or a hardware issue.

Everyone else may want to do the same...

---

### Post by tuebinger on 2009-11-24
I just booted into 64-bit Ubuntu 7.10 using the live CD, which is the OS my daru2 came with and the one I remember the webcam working in for sure.  I pressed the P2 button and the file finder came up again, and  the lsusb output doesn't show the microdia webcam. I checked the keyboard layout to make sure it was 105-key std US layout. 

Any advise as to what to do next?

-Stephen

---

### Post by thomasaaron on 2009-11-25
We're going to need to bring it in for repair.

I've looked back though previous emails to see how we fixed this before, and we ended up having to bring *both* of the previous computers in for repair.

I thought we had fixed one with re-imaging, but... nope.

Email me at support...at...system76...dot...com, and I'll provide further instructions.

---

