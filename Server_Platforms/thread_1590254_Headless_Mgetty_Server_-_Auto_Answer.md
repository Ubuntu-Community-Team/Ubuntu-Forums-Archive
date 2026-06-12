---
title: "Headless Mgetty Server - Auto Answer"
date: 2010-10-07
forum: Server Platforms
---

### Post by TeamXlink on 2010-10-07
Hello.

I have a pc running Ubuntu 8.10 desktop.

My other device has a modem with a phone cord running from that to my pcs modem, which then routes it through my lan.

This is the process I go through.

I start to dial in form my othe device.

I input this command in my bntu Pc's terminal.

Then I input this command

sudo mgetty -D /dev/ttySHSF0 -m

Then I inpuut this command

sudo killall -USR1 mgetty

And it connects.

Some of the software I use doesn't support blind dial, it must receive a dial tone, when I use this software, my setup is like this.

Other Device modem to pc modem via phone cord.

Pc HeadPhone audio out to other modem slot on my pc, the one where you can plug in a telephone.

This is the process I use for this case.

I start to dial in form my othe device.

Play an mp3 dial thats a recording of a dial tone.

I input this command in my bntu Pc's terminal.

Then I input this command

sudo mgetty -D /dev/ttySHSF0 -m

Then I inpuut this command

sudo killall -USR1 mgetty

And it connects.

To get it to detect the false dial tone, I have to mess with the volume on the pc, most of the time I have to run it through external speakers to act as an amplifier.

This is what I want to achieve.

-Completely Headless
-Simulated Dial Tone

I am open to using any version of Linux, or some OS that s not windows.

The closest example of what this is is essentially, a dial up isp.

The phone cord goes from devices into the modems on the pc it has an automatic dial tone and once it connects it routes it through a LAN.

Thank you.

---

### Post by TeamXlink on 2010-10-07
This is a bump.

---

### Post by TeamXlink on 2010-10-09
I already fixed the dial tone part but I still need to get it headless.

This is another bump.

---

### Post by TeamXlink on 2010-10-10
Alright,I think I know how to make  it work but I need to enter multiple modem command strings. These are the command strings I need to use.

```

# resets the modem 
     ATZE1 

# puts the modem into voice mode 
     AT+FCLASS=8 

# opens the connection 
     AT+VLS=1 

# produces the tone 
     AT+VTS=[440,350,255] 

# closes the connection so it can answer 
     ATH 

# answers the connection 
     ATA

```

But I'm unsure of how to do this and I don't think I would be able to run it headless for multiple connections this way unless I made a new init string that is sent from my device to this pc then it interprets it and runs that list of commands.

Thank you.

Bump.

---

### Post by dalitso on 2010-10-10
This might help the auto answer part [http://ubuntuforums.org/showthread.php?t=1535238](http://ubuntuforums.org/showthread.php?t=1535238)

---

### Post by TeamXlink on 2010-10-10
> **dalitso said:**
> This might help the auto answer part [http://ubuntuforums.org/showthread.php?t=1535238](http://ubuntuforums.org/showthread.php?t=1535238)

Thank you  for replying.
Unfortunately, I can't find where mgetty is located for me, it isn't in sbin.

Thank you.

---

### Post by TeamXlink on 2010-10-17
I got it to auto-answer!

Finally!

I still need to figure out how to use the modem command to make the dial tone but I've made good progress.

Does anyone know how to do that?

---

