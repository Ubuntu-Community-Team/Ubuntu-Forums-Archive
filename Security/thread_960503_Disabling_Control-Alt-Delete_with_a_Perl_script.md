---
title: "Disabling Control-Alt-Delete with a Perl script"
date: 2008-10-27
forum: Security
---

### Post by Smatchimo on 2008-10-27
Hi, this is sort of a programming question but not entirely, it has me quite confused.

If I do this, pressing control-alt-delete is immediately disabled, no reboot is required:

/bin/echo "" > /etc/event.d/control-alt-delete
/sbin/telinit q

I'm trying to do this same thing with a Perl script. The file is made a 0 byte empty file just fine, and it runs the "telinit q" command ok without getting any errors back. But Control-Alt-Delete is still not disabled.

If I manually run telinit q, or reboot, then control-alt-delete gets disabled fine.

Does anyone have any idea why Perl seemingly has no effect when it runs "/sbin/telinit q"? Is there an Upstart equivalent of "telinit q" I could be running instead that Perl could run ok too? 

This is happening in Hardy but not Edgy. SELinux is completely disabled and this behavior still happens. 


Thanks!

---

### Post by Smatchimo on 2008-10-29
If no one really knows why a Perl script (ran as root /using sudo), calling `/sbin/telinit q` is having no effect... any idea on a better forum to try asking on?

---

### Post by manpaz on 2008-10-30
I'm not sure why you are trying to get done with perl, but if this could help, I'd like to suggest disable it in xorg.

```

Section "ServerFlags"
Option "DontZap" "Yes"
...
EndSection

```

   Thanks,

---

### Post by Gamma746 on 2008-10-30
> **manpaz said:**
> I'm not sure why you are trying to get done with perl, but if this could help, I'd like to suggest disable it in xorg.

```

Section "ServerFlags"
Option "DontZap" "Yes"
...
EndSection

```

   Thanks,

You're thinking of Ctrl+Alt+Backspace; that won't stop Ctrl+Alt+Delete.

Smatchimo, you might have better luck with a shell script.  Something like ```
 #!/bin/bash
/bin/echo "" > /etc/event.d/control-alt-delete
/sbin/telinit q

```

---

### Post by manpaz on 2008-10-31
That's right, thanks Gamma746. To disable Ctrl-Alt-Delete from system you can edit the /etc/inittab and comment out the action for CTRL-ALT-DEL, it must look like:

```

# What to do when CTRL-ALT-DEL is pressed.
# ca:12345:ctrlaltdel:/sbin/shutdown -t1 -a -r now

```

Note that the prior line is advising about what to do with CTRL-ALT-DEL.

---

### Post by qrst472 on 2008-11-03
The real evils, indeed, of [wow gold](http://www.wowpowerleveling-wow.com/) Emma's situation were the power of having rather too much her own way, and a disposition to think a little [wow gold](http://www.wow-wowpowerleveling.com/) too well of herself; these were the disadvantages which threatened alloy to her many enjoyments. The danger, however, was at [wow power leveling](http://www.powerleveling-wowgold.com/wow-power-leveling.html) present so unperceived, that they did not by any means rank as misfortunes with her. Sorrow came--a gentle sorrow--but not at all in the shape of any disagreeable consciousness.--Miss Taylor married. It was Miss Taylor's loss which first brought grief. It was on the [wow powerleveling](http://www.wow-wowpowerleveling.com/) wedding-day of this beloved friend that Emma first sat in mournful thought of any continuance. The wedding over, and the bride-people gone, her father and herself were left to dine together, with no prospect of a third to cheer a long evening. Her father composed himself to sleep after dinner, as usual, and she had then only to sit and think of what she had lost.weiwei1978123

---

### Post by Smatchimo on 2008-11-11
Is there a certain package to install to enable /etc/inittab? My test Ubuntu 8.04 VM's don't even have that file. 

I'm trying to do this with Perl because I work for a hosting company and we have a little system set up to run scripts on our hundreds of servers each night... This little Perl script is going to make sure control-alt-delete is disabled every day incase it gets re-enabled by someone / somehow. 

I'll try a shell script today instead, but that really shouldn't make a difference I'd think.

---

### Post by kevdog on 2008-11-11
Ubuntu did away with the inittab file in Gutsy.  Its possible you could recreate one and try it that way, or if you want your script commands to be present from boot, you could add the commands to the rc.local file

---

### Post by manpaz on 2008-11-11
then, you can try:
```

perl -pi -e 's/ca/#ca/ if m/ctrlaltdel/' /etc/inittab

```

---

### Post by Smatchimo on 2008-11-11
Ohh freaky. I don't know why this happens, but I figured out what the deal is.

This immediately disables control-alt-delete:

```
echo "" > /etc/event.d/control-alt-delete; 
telinit q;
```

This does not (although once the server is rebooted, control-alt-delete is disabled, but not until then):

```
> /etc/event.d/control-alt-delete; 
telinit q;
```

Doing the echo ends up with a 1 byte file (just a newline).... doing it the other way ends up with a 0 byte file. 

So I tried this, but this goes into effect immediately too, even though it also produces a 0 byte file...

```
rm -f /etc/event.d/control-alt-delete
touch /etc/event.d/control-alt-delete
telinit q
```

I'm guessing this has something to do with how event.d detects if a file has changed or not. ??? Oh well, the script works now, I don't mind not knowing ;-)

---

