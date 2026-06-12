---
title: "Remember authorization / disable password for some actions in PolicyKit"
date: 2009-10-31
forum: Security
---

### Post by LoonyPhoenix on 2009-10-31
Hey, everybody, I need some help tweaking my security options. I tried man pages of PolicyKit and Google, but couldn't find definitive answers, so here I am :)

Can I make some actions available automatically, without the password, with PolicyKit? For example, I don't want to have to enter my password every time I mount a partition. I understand I can configure permanent mounts with fstab, but I'd like to try it this way first :) Also, I would like to give Software Center permission to install and uninstall software without password authorization. And some other things. I understand it's a security risk, but hey, I don't have any sensitive data, and I'm not paranoid (so sue me). It's my call, isn't it?

PolicyKit is supposed to be the new and flexible system for organizing permissions, so I want it to do what I want it to do. But I can't figure out how :)

PS: I'm using Karmic

---

### Post by batsali on 2009-11-01
Same here. In jaunty there was a checkbox to remember authorisation for certain actions, in karmic a can't seem to find how to do that. Frankly, it's becoming very annoying.

---

### Post by cariboo on 2009-11-01
I have had the remember password option when automounting a drive or partition in Karmic since Alpha2. I just did a fresh install yesterday, and the option was still there.

---

### Post by LoonyPhoenix on 2009-11-01
> **cariboo907 said:**
> I have had the remember password option when automounting a drive or partition in Karmic since Alpha2. I just did a fresh install yesterday, and the option was still there.

Well, I don't see it there.
[IMG]https://dl.getdropbox.com/u/12743/authentification.png[/IMG]

---

### Post by pjomega on 2009-11-01
The new policykit-1 which supercedes the old policykit doesn't seem to have a gui for adjusting authorizations. The policies are stored as xml files in /usr/share/polkit-1/actions. 

1) Note the service attempting the action and find the appropriate policy in the actions directory. In your case it's org.freedesktop.devicekit.disks.policy. 

2) Edit the file in your favorite editor and find the right action (e.g., org.freedesktop.devicekit.disks.filesystem-mount-system-internal). 

3) The defaults key controls the access. Check the manpage for polkit for all the details, but **allow_any** controls every client, **allow_inactive** controls clients outside of the currently active session and **allow_active** controls access in the active session. You care about the **allow_active** key

4) Selecting a key value of "*no*" denies access, "*yes*" implicitly permits access, "a*uth_user*" requires user authentication, "*auth_admin*" requires admin authentication. "*auth_user_keep*" and "*auth_admin_keep*" function similarly but retain authentication for a few minutes afterward. Changing the **allow_active** key's value to "*yes*" should stop the authentication demands.

5) Save the file and it should take effect immediately.


Cheers

---

### Post by pocono on 2009-11-01
Thank you pjomega! Works great.

---

### Post by Darce on 2009-11-02
Hi guys,

I started a thread with the same problem here :
[http://ubuntuforums.org/showthread.php?t=1308084](http://ubuntuforums.org/showthread.php?t=1308084)

and was directed to this thread, so here I am !!

I've followed pjomega's instructions, but the file being referred to (org.freedesktop.devicekit.disks.filesystem-mount-system-internal) doesn't exist on my system, or at least, I can't find it with the search tool under 'Places'

Also, the 'Remember Password' option is NOT available on my Authentication dialog box.

Any ideas ?

Cheers,

Tim

---

### Post by mc4man on 2009-11-02
> Any ideas ?

see here for terminal command to edit file, ect (some edits in the link that may come up

[http://ubuntuforums.org/showthread.php?p=8203192#post8203192](http://ubuntuforums.org/showthread.php?p=8203192#post8203192)

---

### Post by Darce on 2009-11-02
Sorry peeps !

Forgot how to read a post properly, on second viewing, I can declare Problem Solved !!!:oops:

Thanks pjomega !!

---

### Post by LoonyPhoenix on 2009-11-02
Thanks, pjomega, that helped tremendously!

---

### Post by matty83 on 2009-11-07
ok did every thing you said but problem when i try to save the edited org.freedesktop.devicekit.disks.policy.xml file it says cannot change you do not have permission root file ? so if i can't save the changes in make how am i supposed to change the file?

---

### Post by LoonyPhoenix on 2009-11-07
> **matty83 said:**
> ok did every thing you said but problem when i try to save the edited org.freedesktop.devicekit.disks.policy.xml file it says cannot change you do not have permission root file ? so if i can't save the changes in make how am i supposed to change the file?

It wouldn't be much of a security system if you could just edit a file to get whatever access you want :) You need to edit this file as root. Do something like this:

1. Press Alt + F2 to open the "Run..." diologue.

2. Enter
```
gksudo gedit /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy
```
Change the path to the file you want to edit

3. Enter your password

4. Edit the file, save it, close the editor

Cheers!

---

### Post by Boibondas on 2009-11-07
Ok LoonyPhoenix now it's clear.

Thanks

---

### Post by ProgX on 2009-11-10
Hello,
I have got a similar problem - when I plug in the USB hard drive, the system automounts it and an icon shows up on the desktop. But the hardrive is mounted with 0700 permissions and I can not figure out how to change this fact. The only solution is to unmount it and then mount with appropriate permissions.

I need to set permissions at least to read for another user called ftp to be able to share some data from the portable harddrive via ftp server. I have tried to put the user to almost all groups, but it also has not worked.

I have tried to change the authorizations stuff in usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy, but it seems to me that my changes has been totally ignored by policykit, even when I rebooted.

Is there any chance to make it work?
Thank you for your responses!
Regards,
     ProgX

---

### Post by Darce on 2009-11-11
When you plug-in your usb drive, are you being prompted for a password ?

---

### Post by ProgX on 2009-11-11
No, I'm not, every USB hard- or flashdrive is mounted automatically without asking the password. But with 0700 permissions only :-(

---

### Post by ProgX on 2009-11-13
Well, problem solved - I went a little step back and reverted to the previous version 9.04. And everything works, including the choice of permissions. I have read a lot of people's reaction in many forums and the result is that the version 9.10 contains a lot of bugs and therefore it needs some time to "grow up". I'm not one of those who give up without a fight, but if there's so many bugs which nobody knows how to solve, then my fight is lost before it has begun.

So I wish luck to everyone and hopefully one day the Karmic Koala will be perfect!

Regards,
      ProgX

---

### Post by Mr.Kappa on 2009-11-15
You saved me pjomega! That was becoming VERY annoying! 
Long life to ubuntu!! :)

---

### Post by bishounen on 2009-11-16
I had the same issue, this fixed it.  NICE!

Ok, new question:  Which numbnut thought changing the authentication system in such a way that it makes it more difficult for the end user would be a good idea?

---

### Post by pocono on 2009-12-08
Just updated today 12-08-09. Devicekit-disks had an update and now the problem of authenticating is back.

I restored an image from 12-05-09 and allowed all updates except devicekit-disks and everything is good. Any suggestions other than not updating devicekit-disks?

---

### Post by kmccormick on 2010-01-13
pocono: Did you go in and redo your edits after updating devicekit-disks?

Files under /usr/share are not generally intended to be configuration files, so the new package would probably overwrite any changes you made there.

Here's hoping these kinds of things get fixed before they call it an LTS.

---

### Post by Hopalong on 2010-01-17
[QUOTE=pjomega;8219205] . . . 

2) Edit the file in your favorite editor and find the right action (e.g., org.freedesktop.devicekit.disks.filesystem-mount-system-internal). 

 But do it as root, otherwise it won't allow a save. In a terminal, cd to the named /usr/share/polkit-1/actions and use:
  sudo gedit org.freedesktop.devicekit.disks.policy 
- then add your password (again!). Now do the edit and save it: using sudo will allow this.

---

### Post by scoon1329 on 2010-01-18
> **pjomega said:**
> The new policykit-1 which supercedes the old policykit doesn't seem to have a gui for adjusting authorizations. The policies are stored as xml files in /usr/share/polkit-1/actions. 

1) Note the service attempting the action and find the appropriate policy in the actions directory. In your case it's org.freedesktop.devicekit.disks.policy. 

2) Edit the file in your favorite editor and find the right action (e.g., org.freedesktop.devicekit.disks.filesystem-mount-system-internal). 

3) The defaults key controls the access. Check the manpage for polkit for all the details, but **allow_any** controls every client, **allow_inactive** controls clients outside of the currently active session and **allow_active** controls access in the active session. You care about the **allow_active** key

4) Selecting a key value of "*no*" denies access, "*yes*" implicitly permits access, "a*uth_user*" requires user authentication, "*auth_admin*" requires admin authentication. "*auth_user_keep*" and "*auth_admin_keep*" function similarly but retain authentication for a few minutes afterward. Changing the **allow_active** key's value to "*yes*" should stop the authentication demands.

5) Save the file and it should take effect immediately.


Cheers

Is there any decent tutorial online that explains about editing the policies in more detail? I've looked through the policykit documentation and it doesn't seem to refer to these files and how to edit them at all unless I'm just not understanding it.

Thanks in advance!

Joe.

---

### Post by mc4man on 2010-01-18
Here is some docu. though maybe a hair outdated
[http://hal.freedesktop.org/docs/PolicyKit/polkit-action.1.html](http://hal.freedesktop.org/docs/PolicyKit/polkit-action.1.html)

While it's possible to edit the actions files (some contain many actions), one needs to be very careful it doing so.
Some combinations of edits will produce unexpected results and or shouldn't be changed. (plus updates can undo them

For the most common desired edit - not have to authenticate mounting of internal partitions for admin. user, the best way is shown here

[http://ubuntuforums.org/showthread.php?p=8542850#post8542850](http://ubuntuforums.org/showthread.php?p=8542850#post8542850)

based on the fix in lucid where it was recognized auth. in this case was unnecessary
[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/465054](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/465054)

 A couple of other edits that are safe to do

[http://ubuntuforums.org/showthread.php?p=8158855#post8158855](http://ubuntuforums.org/showthread.php?p=8158855#post8158855)

---

### Post by wesswei on 2010-06-24
Wow! This is the biggest waste of time ever. 

Who wants to manually edit xml files all day, let alone find the documentation on what text options controls what! Good grief!

If anyone knows about any frontend management tool to this end, you would save many admins some trouble.

I mean I love editing kexts and plists and xmls and confs as much as the next guy, buy the polkit-gnome-authentication gui was THE BEST! 

Nothing in Lynx as of yet... This winblows.

---

### Post by bala150985 on 2011-04-23
WOW man thanks a lot I use Mandrive and this is the file which we need to edit as root:o.

#gedit org.freedesktop.udisks.policy

---

