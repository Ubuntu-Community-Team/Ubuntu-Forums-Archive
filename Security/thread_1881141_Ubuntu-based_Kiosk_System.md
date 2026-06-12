---
title: "Ubuntu-based Kiosk System?"
date: 2011-11-15
forum: Security
---

### Post by Duolos on 2011-11-15
I am looking for some advice on how I would go about building a secure system for a public setting.

Here's what I'm looking for, in a nutshell:

[LIST]
[*]A "guest" account that a user may login to without needing a password.
[*]The ability to restrict nearly ALL aspects of that user.  No access to the filesystem outside their own "/home" directory, no ability to make any changes to the system itself, etc.
[*]After a certain period of inactivity, the user is automatically logged out and their entire "/home" directory is reset to the exact state it was in before they logged in...essentially wiping out any changes they may have made, including browser history, files copied, etc.
[/LIST]

Basically, this will be used within a public setting where guests need to have full access to the internet and also the ability to edit and print office documents from their personal USB drives.  Nothing more, nothing less.

I've already looked at Webconverger (WAY too limited) and Xpud (again, too limited).

Is there a way to install Ubuntu and just create a limited guest account and handle the rest of what I need with scripts?

Any help or signs in the right direction would be highly appreciated!

---

### Post by Duolos on 2011-11-15
I suppose a little info on exactly what this is for may help.

I work in a hotel that has a small business center (2 PCs) that are currently running Windows 7.  Right now it has a demo version of a fairly limited "kiosk" program.

I would like to move both of those PCs to a completely free system running Linux.  Our guests need to be able to have access to the internet and also be able to edit and print their MS Office documents, PDF files and anything else on the internet.

However, since there are privacy and security concerns, we need to wipe out all traces of their activity when they are finished and be ready for the next guest.

If they end up playing around with simple customization options (changing the wallpaper, etc), that's fine; we just need everything to go back to a default setting when they're finished.

---

### Post by kurt18947 on 2011-11-15
I read about an interesting possible solution to your problem. The thought was to not have a hard drive.  Instead, run a liveUSB session from a publicly inaccessible USB drive with no persistence enabled.  You'd somehow have to be sure that the system reboots after each user.  A second issue I could see is how to enable guests to plug in their own USB drives  without being able to screw with the 'system' USB drive.  Perhaps use a publicly inaccessible live CD instead? The problem with that is liveCDs take *forever* to restart.

I've used public Windows PCs in hotels.  There was SO MUCH CRAP running that they were effectively unusable.  But if I need to print something like an airline boarding pass, it was the only game in town.

---

### Post by Duolos on 2011-11-15
> **kurt18947 said:**
> I read about an interesting possible solution to your problem. The thought was to not have a hard drive.  Instead, run a liveUSB session from a publicly inaccessible USB drive with no persistence enabled.  You'd somehow have to be sure that the system reboots after each user.  A second issue I could see is how to enable guests to plug in their own USB drives  without being able to screw with the 'system' USB drive.  Perhaps use a publicly inaccessible live CD instead? The problem with that is liveCDs take *forever* to restart.

I've used public Windows PCs in hotels.  There was SO MUCH CRAP running that they were effectively unusable.  But if I need to print something like an airline boarding pass, it was the only game in town.

Thank you for the reply, Kurt.

I thought about using a LiveUSB, but only briefly.  We will need something to install on the computer hard drives.  We would also like to have an administrator account so that we can update and install additional software as needed.

Wouldn't there be some way to setup a script to run every time the guest account is logged in (or out) that will replace the /home folder with default data that we setup?

**On a side note**, I notice now that this may not be the right forum category for this.  Could someone please move it someplace more appropriate? Thank you.

---

### Post by Lars Noodén on 2011-11-15
KDE has a kiosk tool.  That might be worth a try.

[list]
[*] [http://extragear.kde.org/apps/kiosktool/](http://extragear.kde.org/apps/kiosktool/)
[*][http://techbase.kde.org/KDE_System_Administration/Kiosk/Introduction](http://techbase.kde.org/KDE_System_Administration/Kiosk/Introduction)
[/list]

---

### Post by Jonathan L on 2011-11-15
> **Duolos said:**
> I am looking for some advice on how I would go about building a secure system for a public setting.

Here's what I'm looking for, in a nutshell:

[LIST]
[*]A "guest" account that a user may login to without needing a password.
[*]The ability to restrict nearly ALL aspects of that user.  No access to the filesystem outside their own "/home" directory, no ability to make any changes to the system itself, etc.
[*]After a certain period of inactivity, the user is automatically logged out and their entire "/home" directory is reset to the exact state it was in before they logged in...essentially wiping out any changes they may have made, including browser history, files copied, etc.
[/LIST]

Basically, this will be used within a public setting where guests need to have full access to the internet and also the ability to edit and print office documents from their personal USB drives.  Nothing more, nothing less.

I've already looked at Webconverger (WAY too limited) and Xpud (again, too limited).

Is there a way to install Ubuntu and just create a limited guest account and handle the rest of what I need with scripts?

Any help or signs in the right direction would be highly appreciated!

Hi Duolos

**_Locking Down_**

My approach to this would be to make it irrelevant what the user did, by preventing them doing anything which survives a reboot.  This seems much easier than trying to stop them doing bad things (it's a long list!).

Perhaps it's something you've already discounted ... but for this kind of thing I've had good results from diskless systems running pure memory-disk, or over NFS.  When they log out (or are logged out) the entire system is recreated.   Instead of trying to stop them changing things, you stop any changes from persisting.

This is pretty much the way Easy Internet cafe had their systems, and also some of the larger hotels I've stayed in.

Happy to share more details of PXE boot or the equivalent USB system I've got; ask if you're interested.


**_Automatically logging out_**

 I've not tried any of the following for real but here are some ideas:

Screensavers: It seems straightforward to mutilate a screensaver into a rebooter (look at the files /usr/share/applications/screensavers, each of which contains an exec line, which would seem to just execute some program.  In your case, reboot).

Want-More-Time popups: Make a tiny window program to ask the user if they want more time. Here's a toy I made with zenity (but could also try tcl/tk or similar):
```
#!/bin/sh

while true; do
        sleep 600
        if ! zenity --question --title="Idle Check" \
                --text="Want more time?" \
                --ok-label=Yes --cancel-label=No \
                --timeout=5; then

                if ! zenity --question --title="Last Chance" \
                        --text="Press Yes to get more time, else will reboot" \
                        --ok-label="More Time" --cancel-label="Reboot now" \
                        --timeout=5; then
                        break
                fi
        fi
done
echo reboot here

```You'd launch this as root at startup.  Would need a little work to not reboot if no-one was logged in.

I also took a look at  [autolog]("http://manpages.ubuntu.com/manpages/lucid/man8/autolog.8.html")  but it looks a little fat seems not to have arbitrary command execution.


Hope that's of some use.

Kind regards,
Jonathan.

---

### Post by Duolos on 2011-11-15
> **Lars Noodén said:**
> KDE has a kiosk tool. That might be worth a try.
 
 
Doesn't appear to be working in Kubuntu. I can't get the source to configure; says I'm missing kde-config. Weird, but it looked promising.
 
> **_Locking Down_**
 
My approach to this would be to make it irrelevant what the user did, by preventing them doing anything which survives a reboot. This seems much easier than trying to stop them doing bad things (it's a long list!).
 
Perhaps it's something you've already discounted ... but for this kind of thing I've had good results from diskless systems running pure memory-disk, or over NFS. When they log out (or are logged out) the entire system is recreated. Instead of trying to stop them changing things, you stop any changes from persisting.
 
This is pretty much the way Easy Internet cafe had their systems, and also some of the larger hotels I've stayed in.
 
Happy to share more details of PXE boot or the equivalent USB system I've got; ask if you're interested.

 
That is pretty much what I'm hoping to do. Ideally, I'd like to run some kind of a script when the user logs out that will restore a read-only version of the /home directory. Wouldn't doing that essentially ensure that every change made or files copied will be removed?
 
Is there a way to do that? To, say, copy a /home/guest-backup to /home everytime the user logs out?

---

### Post by Jonathan L on 2011-11-16
Hi again Duolos

> That is pretty much what I'm hoping to do. Ideally, I'd like to run some kind of a script when the user logs out that will restore a read-only version of the /home directory. Wouldn't doing that essentially ensure that every change made or files copied will be removed?I was thinking of restoring the entire system rather than just the user's directory, just in case they did something like manage to overwrite some file or fill up a filesystem.
 
> Is there a way to do that? To, say, copy a /home/guest-backup to /home everytime the user logs out?What you're suggesting isn't terrible however, and looks pretty much catered for in the Gnome desktop system.  Look in /etc/gdm/PostLogin and the sample file says:

```
# Note: this is a sample and will not be run as is.  Change the name of this
# file to <gdmconfdir>/PostLogin/Default for this script to be run.  This
# script will be run before any setup is run on behalf of the user and is
# useful if you for example need to do some setup to create a home directory
# for the user or something like that.  $HOME, $LOGIN and such will all be
# set appropriately and this script is run as root.

```Something along the lines of
```
if [ $USER == "guest" ]; then
  rm -Rf $HOME
  cp -Rp /root/guestprototype  $HOME
fi
```If the guest prototype is under /root, (which is normally 700 root.root), then you can have all the files in their natural permissions and ownership (ie, owned by "guest").

There's also PreSession and PostSession.  Documentation at [Gnome Display Manager Reference Manual]("http://library.gnome.org/admin/gdm/stable/configuration.html.en").  PostSession looks like a candidate for your reboot command.

Hope that helps.

Let us know how you get on.

Kind regards,
Jonathan.

---

### Post by hellfire695 on 2011-11-16
You may want to consider running something more like Debian if this is for a business setting. that way you encrypt the harddisk, so that can't access the filesystem. that in combo with the limited user profile should work to keep them out of trouble. also you could implement selinux for a fine grained approach.

your best though is to look around and keep open mind

---

### Post by Ms. Daisy on 2011-11-16
If you allow people to plug in a flash drive or USB device, how do you stop them from booting from said device?
 
Another thought, what about virtual machines? Have them only able to access a VM, and it reverts to a snapshot after every use.

---

### Post by Duolos on 2011-11-16
> **Ms. Daisy said:**
> If you allow people to plug in a flash drive or USB device, how do you stop them from booting from said device?
 
We can fairly easily lock down USB booting within the BIOS.
 
> **Ms. Daisy said:**
> Another thought, what about virtual machines? Have them only able to access a VM, and it reverts to a snapshot after every use.
 
I did think of using a virtual machine.  However, that would be fairly slow and would require a restart after every user.
 
---
 
Encrypting the file system isn't a huge issue for us, though.  We just want to prevent the guests from making system-wide changes and reverse everything they do when they log out.  I think what Jonathan L mentioned sounds about right; I'll look into that.
 
Thank you!

---

### Post by aysiu on 2011-11-17
I've set up some kiosks for my school's library that use Gofris to lock down the desktop:
[http://www.upubuntu.com/2011/07/install-gofris-on-ubuntu-1104-to.html](http://www.upubuntu.com/2011/07/install-gofris-on-ubuntu-1104-to.html)

Basically, the way I set it up was there is an admin account and then a guest account (it's not the built-in guest account--it's a special account I created).

Then I configured the guest account to be exactly how I want it.

After that, I logged out of the guest account and logged into the admin account and then used Gofris to lock the guest account down.

That "lockdown" basically means they can do whatever they want to the guest account (change wallpaper, change bookmarks, homepage, etc.), but then once you reboot the computer, it's set up to autologin to the guest account, and the guest account is fresh again (old wallpaper, old bookmarks, old homepage).

In *cron*, I set it up so that kiosks reboot every night at midnight automatically, but the library can also manually reboot if there's any kind of "vandalism" on the guest account.

The nice thing is that you can take away the the toolbar applets and make Firefox autostart, and it basically looks as if there's nothing. The savvy Linux user could probably Alt-F2 to do other stuff, but then it'll all go away after a reboot anyway. I haven't explored this, but there may even be ways to disable Alt-F2.

---

### Post by Duolos on 2011-11-17
> **aysiu said:**
> I've set up some kiosks for my school's library that use Gofris to lock down the desktop:
[http://www.upubuntu.com/2011/07/install-gofris-on-ubuntu-1104-to.html](http://www.upubuntu.com/2011/07/install-gofris-on-ubuntu-1104-to.html)
 
Basically, the way I set it up was there is an admin account and then a guest account (it's not the built-in guest account--it's a special account I created).
 
Then I configured the guest account to be exactly how I want it.
 
After that, I logged out of the guest account and logged into the admin account and then used Gofris to lock the guest account down.
 
That "lockdown" basically means they can do whatever they want to the guest account (change wallpaper, change bookmarks, homepage, etc.), but then once you reboot the computer, it's set up to autologin to the guest account, and the guest account is fresh again (old wallpaper, old bookmarks, old homepage).
 
In *cron*, I set it up so that kiosks reboot every night at midnight automatically, but the library can also manually reboot if there's any kind of "vandalism" on the guest account.
 
The nice thing is that you can take away the the toolbar applets and make Firefox autostart, and it basically looks as if there's nothing. The savvy Linux user could probably Alt-F2 to do other stuff, but then it'll all go away after a reboot anyway. I haven't explored this, but there may even be ways to disable Alt-F2.
 
That sounds just about exactly how I want this to be setup.  However, is it possible to make that "reset" after each guest logs out or only when the entire system is rebooted?  (I'm sorry, I'm at work and don't have access to my linux machine)

---

### Post by aysiu on 2011-11-17
> **Duolos said:**
> That sounds just about exactly how I want this to be setup.  However, is it possible to make that "reset" after each guest logs out or only when the entire system is rebooted?  (I'm sorry, I'm at work and don't have access to my linux machine)
I don't think gofris is that sophisticated. I think it has to be a reboot.

---

### Post by Lars Noodén on 2011-11-18
> **Duolos said:**
> That sounds just about exactly how I want this to be setup.  However, is it possible to make that "reset" after each guest logs out or only when the entire system is rebooted?  (I'm sorry, I'm at work and don't have access to my linux machine)

If you backup the guest directory to another location you can use rsync to copy it back.  Put rsync into .xsessionrc so it will run on login.  Use the --delete option to clear any extraneous files.

---

### Post by grg3 on 2011-11-20
I have been doing this type of system locally for about two or three years. The biggest problem is getting people to try Ubuntu. Once they try it and see how reliable an Ubuntu public access computer can be, they like it. First, I want to say that, in my opinion, this is a vast overlooked market for Linux. Many people have a need for a relatively secure public access computer that requires nearly zero monetary investment for software and very little maintenance. At one time, this was being addressed by both the Gnome and KDE development teams, but it has fallen to the side as other issues have taken high priority. I have hopes that someone who has the programming know how will make a free tool for Gnome, KDE , or Unity that simplifies the installation and configuration of kiosk and public access computers. Until then, we can still do it with a little scripting and editing!

I have been using a method derived from this site [http://users.telenet.be/mydotcom/howto/linuxkiosk/intro.htm]("http://users.telenet.be/mydotcom/howto/linuxkiosk/intro.htm") 
This site has been around for a while and even though some information may be a little dated the principles are sound. 

Some of the gnome tools discussed are still available ( for gnome 2), but may not be as useful as they were. (The KDE Kiosk Tool was a great tool in its day for kde3, too) However, the basic concept of creating a frozen configuration for a public user and restoring it is one that is effective and easy to implement.

The first thing to consider is the distro used for the base. Ubuntu works very well, at least in gnome2 versions. Practically, this means that you are limited to Lucid (10.04) at the moment. I have not had great success configuring Unity or Gnome Shell for use as a public access computer. This is mainly due to the lack of configuration tools that easily let you limit access to features for the locked account. This may change as configuration features are added to Unity and Gnome Shell in the future. Since Lucid is still a long term support release it will be good until 2013. If you wish to have a more up to date system, right now, I recommend Lubuntu. It is fast, light and easily configured as a kiosk/public access computer. 

The process is as follows:
[LIST=1]
[*]Install system to one partition (with separate swap)
[*]Create your public access user account
[*]Begin Locking by changing the user shell to "/bin/screen"
[*]Change user permissions as needed
[*]Make changes to applications and user menu as needed
[*]Create folder with user name in admin home
[*]Use the "deep freeze" script to make a backup of user profile to the folder you created
[*]Make changes to gdm to setup autologin, auto restore, etc.
[*]Reboot and system logs into public account
[*]Logout and auto restore "deep freeze" returns user account to saved state
[/LIST]
This is all very similar to what Ofris does. I have developed my own zenity scripts to automate setup and maintenance of the system, but I have not packaged them. I will be happy to share more details with anyone who is interested. Once the public user is configured and the freeze is setup the only other issues are basic security. You can go as extreme as you want here. The main thing to consider is setting and good password on the admin account and consider locking the bios to prevent booting from removable media.

If the system I install on has a large enough hard drive (10gb or greater) I usually create a third partition for backup. I then use Clonezilla Live to create a backup image that can be restored anytime something goes wrong with the system partition.

Hope this is helpful! :) Let me know if you have any questions.

P.S. For a really locked down kiosk, look here:[http://jacob.steelsmith.org/category/section/ubuntu-kiosk-edition]("http://jacob.steelsmith.org/category/section/ubuntu-kiosk-edition")

---

