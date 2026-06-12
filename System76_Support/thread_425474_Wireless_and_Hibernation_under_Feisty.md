---
title: "Wireless and Hibernation under Feisty"
date: 2007-04-27
forum: System76 Support
---

### Post by aay on 2007-04-27
Under Feisty, Network manager cannot connect to any networks after resuming from hibernate.

This has already been reported as a bug here: [https://bugs.launchpad.net/system76/+bug/102655](https://bugs.launchpad.net/system76/+bug/102655)

I was able to resolve this problem under Edgy by using the processes mentioned here: [http://ubuntuforums.org/showthread.php?t=348496&highlight=wireless+hibernate](http://ubuntuforums.org/showthread.php?t=348496&highlight=wireless+hibernate)

None of the procedures listed in the link above seem to fix this problem under Feisty however.  Are others having this problem under Feisty?  System76, are there any workarounds?

Before I figured out how to resolve the problem in Edgy I could do this manually to fix the problem:

"sudo rmmod ipw3945"
"sudo modprobe ipw3945"

And then Network manager would work again.

Now when I do this I get the following:

ERROR: Module ipw3945 is in use

Until this is fixed what is the workaround?

Adam

---

### Post by thomasaaron on 2007-05-08
If the module is still in use, I would think you could just restart NetworkManager with:

> sudo /etc/dbus-1/event.d/25NetworkManger restart

Does that work?


Best,
Tom

---

### Post by AusIV4 on 2007-05-10
I'm having a similar problem on my Gazelle Value (gazv3). Wireless is unavailable after suspending or hibernating, but it's not just network manager - ifconfig shows only eth0 and lo as the only network devices. eth1 doesn't exist.

From what I can tell, it's the same as what aay is experiencing. Tom's suggestion of running ```
sudo /etc/dbus-1/event.d/25NetworkManger restart
``` didn't help.

I've still got my edgy install, but I think this is the last thing keeping me from switching my menu.lst to boot feisty by default.

Help is appreciated.

---

### Post by iba10753 on 2007-05-10
I'm following this thread as closely as my feeble mind will allow because I'm looking at purchasing a new Gazelle Value for occasional work at client offices.  

I recently purchased a Ratel Value and have been moving my Windows application work over to it.  Because of the System76 buying experience and the great support, I want to purchase a System76 laptop.  The issues with suspend and hibernate are a bit concerning, though.  I still consider myself a real noob with Ubuntu so I don't want to have to spend a lot of time diagnosing and fixing features that I think should just work right out of the box.

Is there an end in sight with regard to these features working correctly with the Gazelle Value?

Thanks,
Ben Askew
Houston, TX, USA

---

### Post by AusIV4 on 2007-05-10
For what it's worth, the wireless light on the front of my Gazelle turns off as soon as it suspends on feisty, and doesn't come back until I do a full reboot. In Edgy, it only goes off when I hibernate or shut down.
[EDIT]
I added ipw3945 to  MODULES_WHITELIST in /etc/default/acpi-support, restarted acpid and acpi-support, suspended, the light stayed on, when I restarted, wireless was back.

---

### Post by thomasaaron on 2007-05-10
Please clarify.
Are you saying that white-listing it works in Fiesty? Or is that what worked for you in Edgy?

---

### Post by AusIV4 on 2007-05-10
Whitelisting the module makes wireless work after hibernate / suspend in feisty. It was not necessary in edgy.

---

### Post by thomasaaron on 2007-05-10
OK. Thanks.
I'll pass that to Carl.

I pasted your above post into the bug report.

Best,
Tom

---

### Post by cfischer on 2007-05-14
I've just upgraded to Feisty from Edgy (actually a clean install, but that's another story) and I find that the script I had used to get my Dell Inspiron 5150 laptop to suspend no longer works. I used the info from [this]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend") to get it to wake up, but the wireless is gone - no eth1! From this thread (thanks) I realized that I needed to reinsert ndiswrapper (sudo modprobe ndiswrapper) and then it connects again. 

So here's my question: I've edited /etc/default/acpi-support as suggested - adding ndiswrapper to the MODULES line and also to the MODULES_WHITELIST line, and to each one and not the other. No luck - I still need to manually reinsert ndiswrapper! 

OK, I've added a one-line script to /etc/default/acpid/resume.d and now the wireless resumes. But why doesn't the acpi-support script do that?

I also commented out the LOCK_SCREEN=true line and even tried changing true to false. I cannot get rid of the annoying screensaver login.

What am I missing here?

Thanks,
Charlotte

---

### Post by aay on 2007-05-14
> **AusIV4 said:**
> Whitelisting the module makes wireless work after hibernate / suspend in feisty. It was not necessary in edgy.

This has not been my experience.

Under Edgy I needed to place ipw3945 under MODULES in order to get wireless working after hibernate/suspend.

After I did that it worked fine.

I've added ipw3945 to MODULES_WHITELIST and it makes no difference for me.

I'm afraid that sudo "/etc/dbus-1/event.d/25NetworkManger restart" does not work either.

If I try and unload and reload ipw3945 (a procedure that worked under Edgy) i get: "ERROR: Module ipw3945 is in use"

---

### Post by rumo_orbis on 2007-05-21
i had a similar problem... maybe this can help [http://ubuntuforums.org/showthread.php?t=449881]("http://ubuntuforums.org/showthread.php?t=449881")

---

### Post by hermogene on 2007-05-21
Your solution (whitelisting) worked for my Dell Inspiron 640m… Thanks!

---

### Post by aay on 2007-05-21
> **rumo_orbis said:**
> i had a similar problem... maybe this can help [http://ubuntuforums.org/showthread.php?t=449881]("http://ubuntuforums.org/showthread.php?t=449881")

Thanks rumo_orbis.  Unfortunately this does not seem to work for me.  I'll keep looking for help.  Is anyone else with a Gazelle Pro having this issue?

Adam

---

### Post by digitalbenji on 2007-05-22
I'm having this same problem on a Darter 3 Ultra (little white bad boy).  Whitelisting does not help.  I'm either going to reinstall feisty tonight because I don't think the factory install was done quite right, or, I'm going to install debian etch.  Haven't made up my mind yet.  I'll keep this thread posted though.

---

### Post by H.E. Pennypacker on 2007-05-23
> Before I figured out how to resolve the problem in Edgy I could do this manually to fix the problem:

"sudo rmmod ipw3945"
"sudo modprobe ipw3945"

And then Network manager would work again.

Now when I do this I get the following:

ERROR: Module ipw3945 is in use

Until this is fixed what is the workaround?

When I do sudo rmmod ndiswrapper (I use ndiswrapper), I get the same error message (...is in use).  When I do sudo modprobe ndiswrapper, NOTHING happens at all.  The terminal seems to be thinking away.

> I added ipw3945 to MODULES_WHITELIST in /etc/default/acpi-support, restarted acpid and acpi-support, suspended, the light stayed on, when I restarted, wireless was back.

No luck there.  Adding ndiswrapper to Modules_Whitelist won't work for me.

> OK, I've added a one-line script to /etc/default/acpid/resume.d and now the wireless resumes. But why doesn't the acpi-support script do that?

You probably mean /etc/acpi/resume.d, because there is no /etc/default/acpid/resume.d.  /etc/default/acpid/ is not a directory.

Note:  I don't have a System76 computer, but I share these problems under Feisty.

---

### Post by digitalbenji on 2007-05-24
I actually removed the modules_whitelist for ipw3945, and this has made it so that networking does indeed work after resume/suspend/hibernate return.  So, I think that I must have added the whitelist before even testing this, and assumed that it was broken prior to and after the whitelist. 

Oops.

---

### Post by QuinnStorm on 2007-05-25
In my experience, its simple to get wireless to work on suspend/resume, and its as simple as one of two methods.

#1 - simply toggle the wireless switch off and back on

or

#2 - add a script to /etc/acpi/resume.d that contains the line:
acpitool -n 1

As an addendum to #2, if you have problems where the screen is blank on resume, try making the line read:
acpitool -n 1 -z 15

Of course you have to
sudo apt-get install acpitool

---

### Post by aay on 2007-05-25
> **QuinnStorm said:**
> In my experience, its simple to get wireless to work on suspend/resume, and its as simple as one of two methods.

#1 - simply toggle the wireless switch off and back on

or

#2 - add a script to /etc/acpi/resume.d that contains the line:
acpitool -n 1

As an addendum to #2, if you have problems where the screen is blank on resume, try making the line read:
acpitool -n 1 -z 15

Of course you have to
sudo apt-get install acpitool

Finally a solution that works!!!  Much thanks QuinnStorm.  I can't believe this was staring me in the face the whole time.

Using the toggle switch does the trick.

For those of you unfamiliar with how to do this, just hit "Fn+F2"

Running "acpitool -n 1" doesn't seem to work.  From what I read in the acpitool man page the -n option should do the same thing as toggling wireless off.  But this just doesn't seem to work on the Gazelle.  Does anyone else know how to do this from the command line and automate it when suspending/hibernating?

System76, I think if you configured the wireless card to toggle off by default, this might fix most (all?) of the suspending/resuming/networking problems you are having so it would be great if you could look into it.  Maybe the whitelisting approach should do the same thing, but obviously for me and for some others it isn't working.

Thanks again QuinnStorm!  BTW, are you "the" QuinnStorm of Beryl or another QS?

Adam

---

### Post by grndslm on 2007-05-31
I had to use the whitelisting method in edgy, but I think this solution is more elegant:

EDIT /etc/acpi/resume.d/60-asus-wireless-led.sh
SWAP the 0 and the 1 inside the script

You're good to go!

---

### Post by thomasaaron on 2007-05-31
Brilliant.

Worked for me.

---

### Post by tommie74 on 2007-06-17
My computer with Xubuntu feisty had a problem with getting an ip-adress after waking from hibernation. I´ve solved this problem by changing /etc/default/acpi-support

Editing this file, look for the line below, where to add [networking] after that no problems anymore:

# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="networking"

Hope this will work for you to,
Thomas.

---

### Post by erez001 on 2007-06-28
to rmmod ipw3945 you should :


sudo kill `cat /var/run/ipw3945d.pid`
sudo /bin/rm -f /var/run/ipw3945d.pid
sudo rmmod ipw3945

---

### Post by mojavelinux on 2007-08-08
I can attest to the fact that swapping the 1 and the 0 in /etc/acpi/resume.d/60-asus-wireless-led.sh fixed my problem where the wireless card would not activate after returning from resume in Feisty. I have the Serval from System76.

Prior to this fix, I had to press Fn+F2, wait, and hope for the best. When that did not work, I had a script to kill the ipw3945 process and module and reload. I no longer have to do that.

---

