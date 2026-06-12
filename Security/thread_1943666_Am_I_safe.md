---
title: "Am I safe ?"
date: 2012-03-19
forum: Security
---

### Post by leclerc65 on 2012-03-19
I have several PC/Laptops connected by wired/wireless to my home  router.
All I want is protection for an old laptop, used only for banking, that I have Lubuntu 10.04 installed on it. That laptop is only connected to my bank, all the remote access programs like Vinagre are removed, Firewall is enabled. Can I be sure that that machine cannot be compromised ?

---

### Post by Ms. Daisy on 2012-03-19
There are things you can do to significantly increase the security on that laptop.  But you'll never be 100% certain all the time. 

Start by looking at the [basic security wiki]("https://wiki.ubuntu.com/BasicSecurity"). Look at the sticky threads in this forum as well.

---

### Post by sidzen on 2012-03-19
If the old baknking PC is connected to router only via twisted pairs, it is only on when in use and you turn it off and/or disconnect from internet when not in use, you are relativly safe.  I would just use puppy when i wanted to do online banking and only when absolutely necessary ( see [*this*]("http://ubuntuforums.org/showthread.php?t=1943036") thread ).

---

### Post by sammiev on 2012-03-19
puppy runs from root from what I have tested. If a hacker gets into your root, then they have control. Just my 2 cents. Ms. Daisy posted a great link that can only help.

---

### Post by sidzen on 2012-03-19
> **sammiev said:**
> puppy runs from root from what I have tested. If a hacker gets into your root, then they have control. Just my 2 cents. . .
It's less likely that a hacker will compromise encrypted puppy config files for the short time a transaction with a bank takes than to have a PC's hard drive connected directly to the bank for extended periods of time.  

refs:  [http://lifehacker.com/5381466/use-a-linux-live-cdusb-for-online-banking](http://lifehacker.com/5381466/use-a-linux-live-cdusb-for-online-banking)
         [http://voices.washingtonpost.com/securityfix/2009/10/e-banking_on_a_locked_down_non.html](http://voices.washingtonpost.com/securityfix/2009/10/e-banking_on_a_locked_down_non.html)

---

### Post by Ms. Daisy on 2012-03-20
**Using some other distro live CD is not the answer to securing a Lubuntu machine.** All operating systems need to be hardened if you want to achieve a higher level of security. All of the *buntu flavors can be hardened without introducing any other distro.

A live CD can provide some security benefits. But it doesn't address browser security at all. Your credentials & cookies can still be stolen from your browser in a Live CD as easily as in an installed OS. And it's more secure to run as a user with reduced privileges- puppy runs as root.

---

### Post by Dangertux on 2012-03-20
Here is the thing here. Nobody (at least nobody who knows what they're talking about) is going to tell you that a system can't be compromisd. You are always at risk, however the trick is to minimize that risk as much as possible

As stated a liveCD provides some protection, but not a load more than a well secured standard installation. I would consider reading the basic security wiki, as well as the security stickies.

All in all if you use a sane configuration (good passwords, update regularly etc), no-script, apparmor, and a firewall you should really have nothing to worry about.

---

### Post by leclerc65 on 2012-03-20
**good passwords**   Nope (the machine is in my bedroom, connected wirelessly to my router)
**update regularly** Nope (I hate update, it breaks thing more often than not)
**no-script**        Nope
**apparmor**         Don't know what it is, I have enough headache for two weeks reading about Firewall this morning
**Firewall **        It was set to Deny All Inbound, Allow all Out - but I will try to close all, allow only HTTP

I use Chrome, the Home Page is set to my Bank Address (HTTPS). I do one or two transactions per month, turn the machine off immediately after use. Beside that, all I download is (my) Bank's statements in PDF format.
Am I too paranoid ?:p
So this is a 'single user/single use' machine. I try to find a meaning for its existence other than a garbage dump.

---

### Post by Dangertux on 2012-03-20
> **leclerc65 said:**
> **good passwords**   Nope (the machine is in my bedroom, connected wirelessly to my router)
**update regularly** Nope (I hate update, it breaks thing more often than not)
**no-script**        Nope
**apparmor**         Don't know what it is, I have enough headache for two weeks reading about Firewall this morning
**Firewall **        It was set to Deny All Inbound, Allow all Out - but I will try to close all, allow only HTTP

I use Chrome, the Home Page is set to my Bank Address (HTTPS). I do one or two transactions per month, turn the machine off immediately after use. Beside that, all I download is (my) Bank's statements in PDF format.
Am I too paranoid ?:p,
So this is a 'single user/single use' machine. I try to find a meaning for its existence other than a garbage dump.

Well ... Not to put too fine a point on it but your security posture sucks. I would recommend following the above tips.

Hope this helps.

---

### Post by Ms. Daisy on 2012-03-20
Hmm..   If that is your intended security setup, then I'd suggest the following:

**good passwords**- these apply to every account that has a password, not just your Ubuntu sudo password.  Your wireless router has a password that should definitely be changed from the default (which is probably "password").

**Update regularly**- What is it breaking? What are your specs? Maybe you need a lighter distro?

**noscript**- yeah, no one likes to configure it. But if the only place you're going is the bank website then it will take you roughly 7 seconds to set up.

**apparmor**- this one has a steep learning curve IMO. You'd be more secure with it, but it takes time to figure out.

**Firewall**- Again if you're only going to the bank website, this should be really easy to set up.  Check out [this]("http://ubuntuforums.org/showthread.php?t=1876124") tutorial.

---

### Post by leclerc65 on 2012-03-21
With the exception of AppArmor , I think I can follow these guidelines without much problem...but
1) Updates: the router is at the basement, wireless reception on the second floor of my house is really bad - signal can drop anytime. The only distro that works well is Puppy which was not recommended. If the signal drops while doing a 'sudo apt-get upgrade' it can be a nightmare. Beside, if you get these 'Aw - Snap' messages often from your browser, you know why I hated Updates.

2) I still don't understand the NoScript part. Who can put a bad script there, my Bank itself ? Please remember that I set my Home Page as the Bank's URL, I don't navigate anywhere, I don't even use emails on that machine. So please educate me. But I will do it if you say so.

I should also have mentioned that I do have Mac Address blocking,the Router Admin's password is 8 char long, so the door is not wide opened as it might seem.

Thanks everybody.

---

### Post by Ms. Daisy on 2012-03-21
You may consider boosting the wireless signal so it won't drop out on the second floor.  Maybe you can move the router to a more central location or add a repeater.  Or hardwire the computer to the router.  That's less of a security thing and more of a functionality thing. Losing the signal all the time would drive me nuts.

Who can put a bad script in your bank's website? Scripts make the internet interactive and cool. But scripts can be misused to compromise your browser. Surely your bank has a hardcore team of security experts working to keep the web server safe.  The problem is you don't have any control over what happens to your bank's website.    If you use NoScript, then you can prevent malicious scripts from running in your browser in the event that the bank's website gets cracked.  Honestly this is probably venturing into true paranoia country if  you're really only going to visit the one web page.  But your original question was "Can I be sure that that machine cannot be compromised?" You'll never be totally sure but NoScript will make you a little more sure. 

There are some links in the basic security wiki that go into more detail about what NoScript prevents if you still have questions.

---

### Post by needhelppeeps on 2012-03-22
Increasing the wireless footprint will decrease security further since the signal will be available over a larger area. It is advisable to use the minimum signal you need. It's worth trying to move the attenaeas horizontal instead of vertical. MAC filtering only serves to keep someone honest from accidentally connecting. I would install STP cat5 and use secure transmission protocols such as https, ssh, etc. You should also disable remote management of the wireless on the WAN side and consider restricting management to a single IP on the LAN side and only from a cabled connection. On your switch, disable all ports except the ones you need and turn limit those to known MAC addresses. I would also consider segmenting those ports for any PCs that do not need to "see" each other. Once you've done that, use full disk encryption for your offsite backups and any laptops, at the very least. Purchase cables for the laptops and lock them except when traveling. Laptops are a targeted theft item. You should definitely install NoScript and turn on your Uncomplicated firewall and lock it down to only the ports that must be open. Modify the default apparmor profile for firefox, I found the defaults to be rather open. I found setting up HIDS for a general purpose machine to be too much trouble, but if you have the time to mess with it, it's certainly effective at noting changes. However, if something were created in a frequently updated folder, you likely wouldn't notice as it's not practical to investigate changes in those folders. I suppose you could script flushing of those folders nightly.

---

### Post by MasterGamerJK on 2012-03-22
Use Trucrypt and DONT browse the internet from that machine and that's about all you need : )

PS:  NEVER NEVER NEVER use a public access point.

---

### Post by TheS0urce on 2012-03-24
> **sammiev said:**
> puppy runs from root from what I have tested. If a hacker gets into your root, then they have control. Just my 2 cents. Ms. Daisy posted a great link that can only help.

I agree, that's why I recommend lightweight portable security.  It has no root and you can't mount to any devices.

If you do internet banking, reboot and then do it.  Any infections will be gone.

[http://www.spi.dod.mil/lipose.htm](http://www.spi.dod.mil/lipose.htm)

---

### Post by Ms. Daisy on 2012-03-25
> **TheS0urce said:**
> I agree, that's why I recommend lightweight portable security.  It has no root and you can't mount to any devices.

If you do internet banking, reboot and then do it.  Any infections will be gone.

[http://www.spi.dod.mil/lipose.htm](http://www.spi.dod.mil/lipose.htm) Did you read the rest of the posts in this thread?
**A live CD will prevent malware from being installed permanently, but it will not prevent browser exploits (like your bank and email passwords getting stolen). **

---

### Post by OpSecShellshock on 2012-03-25
I think we're already talking about a single-task, dedicated system. In that sense, using a live CD or USB won't get you anything you're not already getting by having a system entirely dedicated to doing one thing only.

The biggest potential threats for a dedicated system are going to be direct physical access to the machine by another person, weak wireless encryption and/or password, and a router the integrity of which has been somehow compromised (i.e. DNS settings have been maliciously altered). Focus of security effort should be more toward those things.

---

### Post by sammiev on 2012-03-25
> **Ms. Daisy said:**
> Did you read the rest of the posts in this thread?
**A live CD will prevent malware from being installed permanently, but it will not prevent browser exploits (like your bank and email passwords getting stolen). **

+1 no need to add more info!

---

