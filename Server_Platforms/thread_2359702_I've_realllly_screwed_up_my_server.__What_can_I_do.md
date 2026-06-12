---
title: "I've realllly screwed up my server.  What can I do?"
date: 2017-04-26
forum: Server Platforms
---

### Post by jmartino2 on 2017-04-26
**Setup:**
[LIST]
[*]I'm a super-newbie to Ubuntu.
[*]I ordered a new dedicated server running Ubuntu 16.04.
[*]Server is located 1800 miles from my location.
[*]Webhost gave me an admin user *"Justin"* and a password for that user.
[*]After much reading, trial, and error, I finally managed to enable a password for ROOT.
[*]Setup my server apps/websites as needed (ROOT was required).
[*]Everything was great and working properly.
[*]Then (while logged in as ROOT) I disabled the ROOT password with this command:  [COLOR=#ff0000]$ sudo passwd -l root[/COLOR]
[*](I was trying to maintain proper security - that's why I did it.)
[/LIST]
**Problem:**
[LIST]
[*]**&#8203;**Now I need ROOT again, and no matter what I do, I CANNOTTT set the ROOT password!
[*]Using my "Justin" user, every time I try anything with [COLOR=#ff0000]sudo[/COLOR] or [COLOR=#ff0000]su[/COLOR] it kicks me out with errors like:
[LIST]
[*][COLOR=#ff0000]Justin is not in the sudoers file. This incident will be reported.[/COLOR]
[*][COLOR=#000000]and[/COLOR]
[*][COLOR=#ff0000]su: Authentication failure.[/COLOR]
[/LIST]

[*]In other words, since I can't login as ROOT -- I can't do anything as ROOT.
[*]And "Justin" is a worthless looser.  He can't do anything because he's not in the sudoers file (don't know why).
[*]And su authentication is broken (don't know why).
[*]And my server is 1800 miles away.
[/LIST]
**Reference:**
[LIST]
[*]I have been through the tips on all of the following pages (and more), and I'm still stuck.
[*][http://www.tecmint.com/how-to-enable-and-disable-root-login-in-ubuntu/](http://www.tecmint.com/how-to-enable-and-disable-root-login-in-ubuntu/)
[*][https://askubuntu.com/questions/34329/su-command-authentication-failure](https://askubuntu.com/questions/34329/su-command-authentication-failure)
[*][https://linuxconfig.org/enable-ssh-root-login-on-ubuntu-16-04-xenial-xerus-linux-server-desktop](https://linuxconfig.org/enable-ssh-root-login-on-ubuntu-16-04-xenial-xerus-linux-server-desktop)
[*][https://askubuntu.com/questions/34329/su-command-authentication-failurehttps://linuxconfig.org/enable-ssh-root-login-on-ubuntu-16-04-xenial-xerus-linux-server-desktop](https://askubuntu.com/questions/34329/su-command-authentication-failurehttps://linuxconfig.org/enable-ssh-root-login-on-ubuntu-16-04-xenial-xerus-linux-server-desktop)
[/LIST]
**Plea:**
[LIST]
[*]Can anyone help me figure out how to get out of this jam?
[*]I want to put "Justin" in the sudoers file.
[*]I want to fix the su authentication problem.
[*]I want to re-enable ROOT.
[/LIST]

Thank you.

---

### Post by QIII on 2017-04-26
Hello!

Just by way of learning the ropes:  Don't activate the root user.  It's not necessary and can be dangerous.  If some instructions say to do X as root, use sudo to temporarily elevate your priviledges.

Does your provider make a CP available to you?

---

### Post by wildmanne39 on 2017-04-26
*Thread moved to **Server Platforms**.*

---

### Post by jmartino2 on 2017-04-26
Hi QIII.

Thanks for the response.

Not sure what you mean by "make a CP available to you."

There is no GUI, if that's what you mean.  Everything is command line.

They do have an option in my hosting account to power cycle the machine and/or re-provision it.  That's all.

I do remember them saying something about KVI or KMPI or K-something.  But I don't know what that is.

---

### Post by jmartino2 on 2017-04-26
**Update:**
I asked my webhost if they could help me.  The answer was, *"No.  Sorry.  We're an unmanaged provider."*  Exactly what I expected.  
But he also added this:  [I]"If you are experienced in linux you will be able to utilize system rescue in order to reset the password."  

[/I]I don't know what system rescue is, but I'll look into it.

Any other ideas for the following?

[LIST]
[*]I want to put "Justin" in the sudoers file.
[*]I want to fix the su authentication problem.
[*]I want to re-enable ROOT.
[/LIST]

---

### Post by QIII on 2017-04-26
A CP is a control panel.  

Don't enable root.  As I said, it is unnecessary and unsafe for a server exposed to the web.

If you have little invested at this point, reprovisioning may be the most sensible thing since you don't have physical access.

Please ask here before doing things like that again, though!  :)

---

### Post by jmartino2 on 2017-04-26
Hi QIII.

Thanks again.

But I needed root.  Temporarily.  Everyone blindly says "don't do it."   But my application required it and would not work without it.

And then, like an idiot I disabled it too soon.  I should have checked to make sure my "Justin" user was working properly.

So I guess it's utterly foobar'd now and I'm screwed.

I have about 45 or 50 live websites running on the server, so I can't just wipe it and start over.

Anyway, ROOT is disabled.

But now I have [COLOR=#ff0000]**no access to su or sudo whatsoever!**[/COLOR]

Unless someone can help me find a workaround.

---

### Post by QIII on 2017-04-26
We don't say it blindly.  We say it out of experience.  If you are administering your server over SSH, you should doubly not have an active root account.  And you can use sudo su to do anything root can.

What application requires you to be logged in as root?  I've been doing this for years and have never needed to log in as root.

How are you currently accessing the server?

---

### Post by jmartino2 on 2017-04-26
QIII, Please.
I don't want to argue with you.  I'm not here to argue.
All I want to do it fix SU and/or SUDO for my "Justin" user.
That's all.
Please.
Please.

For what it's worth, this server (like all my servers) is setup and provisioned with [http://ServerPilot.io](http://ServerPilot.io).  It's a server administration system that makes setting up and running LOTS of websites a dream.  It's a modern, faster, slimmer version of cPanel, Plesk, etc...  But it REQUIRES root to get it setup.  Then once it's set, you can disable root again.  No problems.

This is the first time I've ever run into this situation where SUDO isn't working.  After all... it WAS working!  How else could I have enabled root in the first place?

---

### Post by lisati on 2017-04-26
@jmartino2: I think there seems to be a little bit of confusion here about what the various  technical terms mean. The "root" account is something different to using "sudo" to temporarily elevate privileges. While waiting for someone more knowledgeable than myself to step in, you might want to have a quick read of [this]("https://help.ubuntu.com/community/RootSudo") page.

---

### Post by jmartino2 on 2017-04-26
Hi lisati.

I appreciate your reply.  And thanks for the link!

A few days ago I didn't understad *any* of this stuff.  But after going through this fiasco, I believe I do understand most of the concepts discussed on that page.

But the most important thing at this point, is that *somehow* I have lost all access to sudo.  
Something as simple as flushing old kernels out of my boot disk  - (sudo apt-get autoremove) - is totally impossible for me.

I SWEAR I did not erase myself from the sudoer file -- because I literally didn't know there WAS a sudoer file.  So I have no idea how this happened.

...and even less about how to fix it.

---

### Post by CharlesA on 2017-04-27
Hi, What provider are you using for your dedicated server? The majority of them provide some sort of out-of-band access for cases like this or in the event you want to reinstall the OS on the server.

---

### Post by QIII on 2017-04-27
Most outfits like that offer some sort of "emergency control panel/management tool" that gives you temporary sudo capability.  Are you sure you don't have that?  You will need some sort of access to fix this.

And I'm not trying to argue, either.

---

### Post by jmartino2 on 2017-04-27
AAAAAAARrrrrrrrrrrvghhhhhhhhhhhhhhhhh...............
I am so freaking angry.  I have literally spent 15 hours today trying my level best to work out this problem.  I literally hate and detest all this circa-1975 gobbldegook command line crap!!!!!   Why does it have to be so impossibly difficult?!?!?!?!?  I'm not a stupid guy.  But I'm literally RAGIING OUT OF MY MINDDDDDD........GRRRRRRRRRRRRRRRRRERTGYGHdrfR.

ALL I'm trying to do is re-enable SUDO access for my user!  That's all!  Not fly a rocketship to Mars.....  Not rebuild the Great Wall of China......  Just reset a FREAKING PERMISSIONNNNNNN!!!!!!

To that end, I finally researched and read enough to understand that I need a KVM connection to my server.  So I asked my host to hook me up.  They did it fast.  Awesome!

But what do I have when I open the KVM connection??  Nothing.  As in NOTHING.  A black screen.  That's all.

So I pressed a key.  And OH!  GREAT!  More cryptic white writing/gibberish that means absolutely nothing to me!

And I realize... I LITERALLY DON'T KNOW HOW TO REBOOT THIS SERVER!!!!!!!

There's no off button.  No help guide.  NOTHING.  Just black emptiness and gibberish.

AAAAAAGggggg!!!!!!!!!

It won't let me login as "Justin."  And even if I did, I don't think I have proper permissions to proceed.  I can't login as root, because -- no password.  There's no discernable way to EVEN REBOOT THE MACHINE!!!!!!!

God I hate this with all my passion.

So back to Googling ---- again ----  "how to reboot ubuntu over kvm" --- absolutely no help whatsoever.  45 minutes searching and reading and sorting through IRRELEVANT CRAP and I still cannot fathom how to reboot my server.

I'm done.

---

### Post by jmartino2 on 2017-04-27
Call 1969 and tell them they can have their so-called operating system back.

[IMG]http://i.imgur.com/PDDlMOM.gif[/IMG]

---

### Post by darkod on 2017-04-27
Sorry, but part of your issues are because of the support your provider is offering (or not). So don't blame everything on ubuntu or linux.

And first of all if you want this fixed, you have to stay calm, because exactly in situations like this you can mess it up much more (there is always much more to mess up!!!).

What you need now is a way to reboot the server while using KVM or similar console. They already provided you KVM access. When you reboot it, you have about 3secs in the grub menu to boot the Recovery Mode option (not the normal ubuntu option). Sometimes the recovery mode might be under Advanced Option, it depends.

If you get that far, you should get a recovery menu, in it select "drop to root shell". In the shell you will be able to add justin to sudo group, and even to reset root password.

---

### Post by jmartino2 on 2017-04-27
Hello darkod.

Thank you for your thoughtful reply.

I'm soothing my mental wounds in a nice, cold adult beverage.

So I'm a little calmer now.

Yeah.  What you wrote seems so simple!  That's partially why I'm so flabbergasted.  Seriously.  Honestly.  It can't be this hard!

But what you're saying is that there has to be some other (external?) way to reboot the server -- while I'm still looking at the KVM?

That makes sense, but the idea never crossed my mind.  I will ask them.

Thank you again, darkod.

---

### Post by darkod on 2017-04-27
FYI, once you manage to get into the console, here is a nice guide: [https://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](https://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password)

They only reset the password, in your case you want to add justin to sudo group. Something like:
```
usermod -aG sudo justin
```

You can also reset justin pass if you want to.

And don't forget to remount root partition as read-write, exactly like the guide says. That is very important step because the root shell by default is read-only.

---

### Post by Habitual on 2017-04-27
dedicated server often implies a lot.

```
su - root
``` may provide relief, if it hasn't been tried.

Dedicated Server may mean IPMI access.

wrt: "maintain proper security" 
usual method is to add justin to visudo as root and work as justin.

[https://serverpilot.io/community/articles/how-serverpilot-works.html](https://serverpilot.io/community/articles/how-serverpilot-works.html) seems to be the CP or Control Panel.

---

### Post by jmartino2 on 2017-04-27
> **darkod said:**
> FYI, once you manage to get into the console, here is a nice guide: [https://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](https://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password)

They only reset the password, in your case you want to add justin to sudo group. Something like:
```
usermod -aG sudo justin
```

You can also reset justin pass if you want to.

And don't forget to remount root partition as read-write, exactly like the guide says. That is very important step because the root shell by default is read-only.Yes. Thank you for that link, darkod.  I have been reading and cross referencing that guide for hours just to educate myself about the procedure.

But once I got the KVM setup, I couldn't even figure out how to REBOOT!  Ridiculous.  :mad:

So that's the question.  Is it possible to reboot from within the KVM interface?  How?

If not, I plan to try this procedure:


[LIST=1]
[*]Login to the KVM
[*]Look at the pretty blank/black screen
[*]Use my webhost's PowerCycle feature to reboot the machine -- the feature is located inside my webhost's online control panel
[*]While rebooting, hold the [shift] button on my computer to trigger recovery mode inside the KVM
[*]When I see the GRUB screen, drop into root shell
[*]I should now see a command prompt, right?
[*]Mount the root partition with: ( [COLOR=#FF8C00]mount -o rw,remount /[/COLOR] )
[*]Since I have a /boot partition and a HW RAID10 (4x1TB) I may also need to run this? ( [COLOR=#FF8C00]mount --all[/COLOR] )
[*]Then run ( [COLOR=#FF8C00]adduser justin sudo[/COLOR] ) to fix my missing sudoer.
[*]Then run ( [COLOR=#FF8C00]passwd root[/COLOR] ) to enable root and create a password.
[*]Then type ( [COLOR=#FF8C00]exit[/COLOR] ) to get back to the GRUB menu, where I can initiate a reboot.
[/LIST]

darkod, you suggested ( [COLOR=#ff8c00]usermod -aG sudo justin[/COLOR] ) instead of ( [COLOR=#ff8c00]adduser justin sudo[/COLOR] ).  Should I assume that you are correct, and the info from the other site is wrong?

Other than that, #3 and #4 is where I'm stuck.  Is power cycling the machine through the webhost's control panel REALLY the correct method!?  That seems absurd to me.  I can't believe there's not a way to reboot from within the KVM interface.

Am I correct in assuming this exact procedure will take my server offline for 4-5 minutes, and all my websites will be safe?

---

### Post by darkod on 2017-04-27
I think adduser will work too. There are more ways to do it, I simply use usermod but it doesn't mean that's the only way.

As for power cycle in KVM, it should be possible because the point of KVM console is to give you access like you are sitting in front of physical server. But again, not all KVM interfaces are the same, so it will depend on what interface the provider provides you with.

If you have HW raid that would be assembled before you even see the grub menu, so you don't need to remount any of it. /boot should also mount automatically in the root shell I think, so you shouldn't need to remount it.

If the KVM does not offer clear way of reboot, then your idea to powercycle through the web interface while connected to the KVM is worth the try. I'm also not sure you will need Shift, that is when the grub menu is hidden. On servers by default it does show with a 3sec counter. And don't forget that often you need to click inside the KVM window first so that keyboard hits are tranferred to the virtual server instead of being applied to your local PC only. That also depends on the KVM, if it is active right away or after a click inside.

The site content should be safe and power cycle of a physical server might be longer than 5mins. Sometimes up to 10mins although linux reboots much faster than windows.

---

### Post by jmartino2 on 2017-04-27
Wow darko...

Thank you.  Really.

That is a dandy reply.  It's clear, covers my questions well, and it makes sense.

I really appreciate it.

I'll give it a try and let you know how it goes.

---

### Post by jmartino2 on 2017-04-27
**Update:**

CTRL+ALT+DEL does reboot the machine.  Hallelujah!

But the GRUB menu never appears.  

Holding the [shift] button and/or rapid toggling the [shift] button does not trigger the GRUB menu.

I have tried clicking inside the KVM window to make sure I'm sending keystrokes through.

So are there any other super-secret-mysterious hoops I must jump through to get the GRUB menu to appear?

---

### Post by jmartino2 on 2017-04-27
[B]Update 2:

[/B]So I finally got to GRUB.  Had to use the built-in soft keyboard in the KVM.

And I *think* I got the Justin user properly sudoer'd.

But when trying to set a root password, I get this error:

passwd: Authentication token manipulation error
passwd: password unchanged


...back to Google to see what that's all about.

---

### Post by jmartino2 on 2017-04-27
[B]Update 3:

[/B]It's WORKING!  It's WORKING!  It's WORKING!  It's WORKING!

And I'm the happiest guy in UbuntuForums land right now.

Happy Happy Happy.

Since I managed to get "Justin" back into the sudoers file, I decided to just set the root password through SSH and sudo.  It worked great.

Sudo is working.
Root is working.
I have a 35 character password for Root.

My server is online.

No data lost or broken.

[COLOR=#ff0000]**Thank you darkod and everyone else who contributed to this thread!**[/COLOR]

Couldn't have done it without you.

---

### Post by jmartino2 on 2017-04-27
One last question... Do I need to reboot the machine again to "unmount" the drives?  Or something like that?

In other words, earlier, I ran this:  [COLOR=#FF8C00]mount -o rw,remount /

[/COLOR][COLOR=#000000]Should I do something to correct that?[/COLOR]

---

### Post by darkod on 2017-04-28
No, that only mount root as RW which is the standard state anyway. But if you want to, and to check if everything will continue working after a reboot, you can reboot the machine at hours of low traffic for your websites.

Glad you got it sorted. If all is good you can mark the thread as solved, you can do this in Thread Tools above the first post.

---

### Post by TheFu on 2017-04-28
Might want to setup a GUI connection to the KVM host, if you can.  **Virt-manager** is the tool for that. [https://virt-manager.org/](https://virt-manager.org/) it is in the ubuntu repos. Install it on your client, assuming you use Linux. Don't think there are clients for Windows or OSX, but I honestly don't know. Don't know if your provider will allow that level of access - I wouldn't.

For small-scale operations, vmm, is all we need to create and configure new VMs.  Of course, to manage them day to day, I use ssh and sudo.  No need for any root login. sudo is sufficient for everything, seriously.

---

