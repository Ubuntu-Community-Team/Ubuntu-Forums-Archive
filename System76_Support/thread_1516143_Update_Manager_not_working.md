---
title: "Update Manager not working"
date: 2010-06-23
forum: System76 Support
---

### Post by stangdaman on 2010-06-23
I keep getting reminders from update manager that I have quite a few updates that need to be done. when I tell it to install them and put in my password it starts to read the repositories and then just stops and doesn't install anything. Any ideas on what is going on with this would be appreciated.

---

### Post by isantop on 2010-06-23
In lucid, the authentication system does not inform the user if the password was typed incorrectly. Make sure you are typing your password exactly the way it should be, and ensure that caps lock (and numlock on laptops) is off.

---

### Post by stangdaman on 2010-06-23
I am and am able to use it for other things but when I try to update it takes the password and starts to apply the updates then just stops.

---

### Post by Sander1979 on 2010-06-24
I am having the same problem.

Edit: password mixup, problem solved.

---

### Post by jdb on 2010-06-24
> **stangdaman said:**
> I am and am able to use it for other things but when I try to update it takes the password and starts to apply the updates then just stops.

Try:

```

sudo apt-get update
sudo apt-get upgrade

```
jdb

---

### Post by stangdaman on 2010-06-24
When I try to run 

sudo apt-get update

I get the following message:

Could not locate any suitable fingerprints matched with available hardware.

---

### Post by jdb on 2010-06-24
> **stangdaman said:**
> When I try to run 

sudo apt-get update

I get the following message:

Could not locate any suitable fingerprints matched with available hardware.

Do you have a fingerprint reader enabled??

jdb

---

### Post by stangdaman on 2010-06-26
Crap. Yes, well I tried to enable it last weekend but it hasn't really been working right. I just tried to use that instead and it didn't do anything. If I put things back the way they were before I probably should be able to run the update by entering my password I'm assuming.

---

### Post by stangdaman on 2010-06-26
Ok, one more problem. I tried setting things back to the way they were before I made the changes listed here:

[http://knowledge76.com/index.php/Fingerprint_Reader_Usage](http://knowledge76.com/index.php/Fingerprint_Reader_Usage)

to enable the fingerprint reader but it's not taking my password and it keeps asking for the fingerprint. The fingerprint reader is not working either. Any ideas?

---

### Post by jdb on 2010-06-26
> **stangdaman said:**
> Ok, one more problem. I tried setting things back to the way they were before I made the changes listed here:

[http://knowledge76.com/index.php/Fingerprint_Reader_Usage](http://knowledge76.com/index.php/Fingerprint_Reader_Usage)

to enable the fingerprint reader but it's not taking my password and it keeps asking for the fingerprint. The fingerprint reader is not working either. Any ideas?

I've never fooled with the fingerprint reader, can't help you there.
If no one answers sooner, the system 76 techs will be back on line Monday (Colorado time zone).

jdb

---

### Post by RedRat on 2010-06-27
> **isantop said:**
> In lucid, the authentication system does not inform the user if the password was typed incorrectly. Make sure you are typing your password exactly the way it should be, and ensure that caps lock (and numlock on laptops) is off.
I am curious as to why the NUMLOCK key must be off? How would that affect what is typed in from standard part of the keyboard? Is there some connection in how keys are read?

---

### Post by jdb on 2010-06-27
> **RedRat said:**
> I am curious as to why the NUMLOCK key must be off? How would that affect what is typed in from standard part of the keyboard? Is there some connection in how keys are read?

NUMLOCK on a laptop usually causes a group of center keys to produce numbers instead of letters.

jdb

---

### Post by isantop on 2010-06-28
Please post the result of:
```
cat /etc/pam.d/common-auth
```

---

### Post by stangdaman on 2010-06-28
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
auth    sufficient      pam_fprint.so
auth	[success=1 default=ignore]	pam_unix.so nullok_secure
auth	[success=1 default=ignore]	pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login try_first_pass
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth	optional	pam_ecryptfs.so unwrap
# end of pam-auth-update config

---

### Post by isantop on 2010-06-29
> **stangdaman said:**
> 
auth    sufficient      pam_fprint.so


Found the problem.

Try removing this line, so your file looks like:

```

#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.). The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules. See
# pam-auth-update( for details.

# here are the per-package modules (the "Primary" block)
auth	[success=1 default=ignore]	pam_unix.so nullok_secure
auth	[success=1 default=ignore]	pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login try_first_pass
# here's the fallback if no module succeeds
auth	requisite	 pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required	 pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth	optional	pam_ecryptfs.so unwrap
# end of pam-auth-update config
```

---

### Post by RedRat on 2010-06-29
> **jdb said:**
> NUMLOCK on a laptop usually causes a group of center keys to produce numbers instead of letters.

jdb
That may be the case with some computers but pray tell which ones. I have the NUMLOCK key on, but have never seen the standard keys on the KB do anything strange. Yes, the arrow keys have an added function with the blue Fn key. But this is there regardless. I have just never seen that behavior, maybe some more detail.

---

### Post by msrinath80 on 2010-06-29
If your password does not entail the letters/characters that are affected when you activate numlock, then obviously you will never see any difference.

---

### Post by jbelmonte on 2010-06-30
> **RedRat said:**
> That may be the case with some computers but pray tell which ones. I have the NUMLOCK key on, but have never seen the standard keys on the KB do anything strange. Yes, the arrow keys have an added function with the blue Fn key. But this is there regardless. I have just never seen that behavior, maybe some more detail.

Many smaller form factor laptops do not have a separate number pad. Those laptops retask a group of alpha keys to mimic a number pad for rapid data entry when the numlock key is pressed. If your laptop has a separate number pad, then pressing the numlock key will not impact the main alpha keys.

---

### Post by RedRat on 2010-06-30
> **jbelmonte said:**
> Many smaller form factor laptops do not have a separate number pad. Those laptops retask a group of alpha keys to mimic a number pad for rapid data entry when the numlock key is pressed. If your laptop has a separate number pad, then pressing the numlock key will not impact the main alpha keys.
OK that makes sense. Thanks for the explanation, I thought it might apply to all laptops.

---

### Post by stangdaman on 2010-06-30
How do I edit that? Just open it in gedit? What's the terminal command to do that again?

---

### Post by isantop on 2010-07-01
Yep, just use gedit.

The command is:
```
gksudo gedit /etc/pam.d/common-auth
```
Then find the line and replace it. Reboot, and you should be good to go.

---

### Post by stangdaman on 2010-07-02
It won't let me edit that file. It keeps asking for my password and it won't take it when I enter it.

---

### Post by jdb on 2010-07-03
> **stangdaman said:**
> It won't let me edit that file. It keeps asking for my password and it won't take it when I enter it.

WOW, catch 22.
You need to be root to fix the problem of not being able to log in as root.

Try booting to a live CD and mounting the partition.
You should then be able to use sudo to edit the file.


jdb

---

### Post by stangdaman on 2010-07-15
Sorry, it's been a week or more since I responded to this. I'm not sure if I know how to mount a partition from the a live disc. Am I basically reinstalling the OS if I'm doing that? If so that makes me a bit nervous. Aren't there somethings that are pre-installed by system76 for this laptop? If I had installed it myself I probably would have done that right off. I'm really wishing I hadn't tried to get the fingerprint reader working.

---

### Post by jdb on 2010-07-15
> **stangdaman said:**
> Sorry, it's been a week or more since I responded to this. I'm not sure if I know how to mount a partition from the a live disc. Am I basically reinstalling the OS if I'm doing that? If so that makes me a bit nervous. Aren't there somethings that are pre-installed by system76 for this laptop? If I had installed it myself I probably would have done that right off. I'm really wishing I hadn't tried to get the fingerprint reader working.

Mounting a partition just makes it visible, it doesn't change anything.
Once the partition is mounted you can access files on it, edit them , etc.
I'm thinking the the Live CD might even mount them automatically now.

After booting go to Places in the top menu bar & see if they show up there.

jdb

---

### Post by stangdaman on 2010-07-16
I think it is already mounted then. I'm sorry if this is really dense. I'm sure I'm just not understanding. I can access the file from outside of the terminal or pull it up in the terminal but if I try to edit it it wants the sudo password but won't let me enter the sudo password because it keeps looking for the fingerprint. I'm not really sure why it's not taking the fingerprint either because I did run the fingerprint setup and it has saved one but it just isn't recognizing that either.

---

### Post by jdb on 2010-07-17
> **stangdaman said:**
> I think it is already mounted then. I'm sorry if this is really dense. I'm sure I'm just not understanding. I can access the file from outside of the terminal or pull it up in the terminal but if I try to edit it it wants the sudo password but won't let me enter the sudo password because it keeps looking for the fingerprint. I'm not really sure why it's not taking the fingerprint either because I did run the fingerprint setup and it has saved one but it just isn't recognizing that either.

I don't know anything about the fingerprint reader,
but unless it's changed something in bios,
when you boot from a Live CD it shouldn't be asking for a fingerprint.
If it's done something to bios that's scary.

jdb

---

### Post by stangdaman on 2010-07-22
It's not that I can't access it through the live cd I was just trying to understand what I'm doing and why that helps. What you're saying, if I'm understanding correctly, is that the live CD won't have the security that the normal OS has and that I can mount the partition to the live cd makes it able to be edited from within the live cd. Is that right? As I said I'm sorry for being so dense with this I just don't really know a lot of the terminology so I'm just trying to understand the solution.

Also, once it's mounted is there any special command that I have to use to make it edit and save the file to the current location rather than trying to make a change that will be erased once I boot back up normally?

---

### Post by stangdaman on 2010-07-22
Ok, I am running it from the live cd but every time I try to open the file it comes up as read only. It won't let me log in as su I just keep getting an Authentication failure message.

Nevermind, I was able to edit the file so that it looks like what Isantop said. It's no longer asking for my fingerprint but it still won't take my password. I have no idea what the heck happened here. It will use it for one thing and not another. I even tried logging in from the recovery screen and editing the password to make it what I want and it saves it says everything is fine and than when I get into the normal OS it won't accept it. This is absolutely driving me frickin crazy.

---

### Post by jdb on 2010-07-22
> **stangdaman said:**
> Ok, I am running it from the live cd but every time I try to open the file it comes up as read only. It won't let me log in as su I just keep getting an Authentication failure message.

Your getting very close :)

```
sudo gedit /etc/pam.d/common-auth
```

should let you edit it.

jdb

---

### Post by jdb on 2010-07-23
> **jdb said:**
> Your getting very close :)

```
sudo gedit /etc/pam.d/common-auth
```

should let you edit it.

jdb

OOPS!!!

I gave you the wrong path.

/etc/pam.d/common-auth is on the live CD.

The path you need is something like:

/media/some-directory/etc/pam.d/common-auth

If you don't get it before I get home tonight, I'll boot to
a live CD and see what it is.

jdb

---

### Post by jdb on 2010-07-23
> **jdb said:**
> OOPS!!!

I gave you the wrong path.

/etc/pam.d/common-auth is on the live CD.

The path you need is something like:

/media/some-directory/etc/pam.d/common-auth

If you don't get it before I get home tonight, I'll boot to
a live CD and see what it is.

jdb

After booting to a live CD this is what I found.

I opened a terminal by going to the upper left hand corner of the screen and selecting:
Applications > Accessories > Terminal

I then typed in:
```
ls /media
```
and saw nothing.

I next selected:
Places > Removable Media
and saw all my partitions.
I click on one and was able to browse it.


I then tried:
```
ls /media
```
again and saw the partition I had browsed, browsing it had cause it to auto mount.

I've labeled all my partions so they showed up as having names,
yours might just be called something like sda1, I don't know.
The partition on my computer that I accessed was named Ubuntu,
substitute the name of your partition in the next example.

I then typed into the terminal:
```
sudo gedit /media/Ubuntu/etc/pam.d/common-auth
```
and was able to edit it.


jdb

---

### Post by stangdaman on 2010-07-25
I was finally able to edit it. I just opened gedit through as sudo and then navigated to the file through the gui. It let me edit it and it's no longer giving me the issue of asking for the fingerprint reader instead of my password. However, it still won't accept my password. I even tried resetting it through recovery mode and it still won't take it. It's getting there but I still can't update.

---

### Post by thomasaaron on 2010-07-26
When you say it won't accept your password, do you mean that it tells you you've entered an incorrect password, or that typing in the password doesn't return an error but will not make update manager work?

---

### Post by stangdaman on 2010-07-29
> When you say it won't accept your password, do you mean that it tells you you've entered an incorrect password, or that typing in the password doesn't return an error but will not make update manager work? 

I mean both actually. If I try to use that password in update manager it just doesn't do anything. If I try to use it in the terminal to accomplish pretty much anything I get an incorrect password error. I'll try to duplicate it this evening and post the actual error message.

---

### Post by stangdaman on 2010-08-01
Yeah, if I try to become sudo for instance in the terminal I just keep getting a please try again until it locks me out.

---

### Post by stangdaman on 2010-08-02
Just thought I would give this a little bump.

---

### Post by jdb on 2010-08-02
> **stangdaman said:**
> Just thought I would give this a little bump.

You said earlier in the thread that you tried the recovery mode
but you might try it one more time since you got rid of the finger print stuff.

If that doesn't work I'd be thinking about a system reload.

jdb

---

### Post by isantop on 2010-08-03
Yeah, I'd agree on that. A system reload may be faster, unless you chose to encrypt you home directory.

---

### Post by stangdaman on 2010-08-15
I know it's weeks between posts here. I haven't had a ton of time on my hands lately to mess with this. It is starting to get slightly irritating though. 

I tried changing the password again through recovery mode. The part that is really confusing about this is that it keeps saying it's accepting the password but when I reboot and try to use it it doesn't work. Yet again I wish I had never messed with the stupid fingerprint reader as that seems to have started this. Changing it in recovery mode seems to have made things worse too because always before it asked me for my password on boot up which it used to unlock the network keyring. It's not asking for it now and I can't unlock the network keyring because it won't accept the new password so that laptop can't even get online anymore. I swear all I did was enter the password twice and reboot. I didn't even touch any other settings. 

I'm fine with doing a system reload and probably would have done it right from the beginning but it makes me a bit nervous because aren't there a bunch of proprietary drivers that were loaded by System76 for this laptop that now won't be there if I just use a regular ubuntu disc?

---

### Post by RedRat on 2010-08-15
> **stangdaman said:**
> I know it's weeks between posts here. I haven't had a ton of time on my hands lately to mess with this. It is starting to get slightly irritating though. 

I tried changing the password again through recovery mode. The part that is really confusing about this is that it keeps saying it's accepting the password but when I reboot and try to use it it doesn't work. Yet again I wish I had never messed with the stupid fingerprint reader as that seems to have started this. Changing it in recovery mode seems to have made things worse too because always before it asked me for my password on boot up which it used to unlock the network keyring. It's not asking for it now and I can't unlock the network keyring because it won't accept the new password so that laptop can't even get online anymore. I swear all I did was enter the password twice and reboot. I didn't even touch any other settings. 

I'm fine with doing a system reload and probably would have done it right from the beginning but it makes me a bit nervous because aren't there a bunch of proprietary drivers that were loaded by System76 for this laptop that now won't be there if I just use a regular ubuntu disc?
You may well want to contact System76 and ask that question with the technical reps. While I haven't looked at my Serval Laptop, I believe that in the later versions of Ubuntu, there is a "recovery partition"--I may well be wrong about this. Nevertheless you may want to contact the company directly.

---

### Post by stangdaman on 2010-09-11
I broke down and did a fresh install but System76 support page says to go to 

> System > Administration > Hardware Drivers to install nVidia's or ATI's proprietary driver

to install my graphic drivers. When I do that there's nothing there. Is there a repository that I need to add first?

---

### Post by RedRat on 2010-09-11
> **stangdaman said:**
> I broke down and did a fresh install but System76 support page says to go to to install my graphic drivers. When I do that there's nothing there. Is there a repository that I need to add first?
I really suggest that you get in touch with System76 tech reps, do it their way first before trying something on your own or by someone else's suggestion. I would think that when you got your computer, the necessary repos were already included.

---

### Post by stangdaman on 2010-09-13
I actually was following their direction on that. It showed up. I just was being a bit impatient. I've got everything, pretty much, set back up. The process was pretty quick. I wish I had just done that from the start. Thanks for the help.

---

