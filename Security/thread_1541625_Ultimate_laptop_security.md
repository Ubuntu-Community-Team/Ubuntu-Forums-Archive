---
title: "Ultimate laptop security?"
date: 2010-07-29
forum: Security
---

### Post by iceman_ch on 2010-07-29
Here is what I am trying to accomplish.  Tell me what you think or what I can improve.  I also need a little help in implementing some of it.

I want the login to require three things.
Fingerprint
Specific Thumb Drive
Password
When I unplug the thumb drive the system should lock.
When my cell phone moves out of range of the blue tooth I want it to lock.  In case I forget to pull the thumb drive.
I want home folder to be encrypted.
I have the thumb drive partly encrypted and this is where backups of keys are stored.
When I plug in the thumb drive I want an encrypted folder to be mounted and unencrypted automatically.
Set up App Armor along with HDIS.

I have the login working except for the fingerprint reader.  I've done it before I just haven't messed with it yet. I haven't set up the cell phone yet but, I'm reading the tutorial on it right now. I'm also working on the ecrptfs tutorial.  It seems like it will provide everything I need for the home folder.  If the password is reset you still won't have access to the home folder.  I'm running into my first problem with the automatic mounting and decrypting of a folder.  I have truecrypt installed for this purpose.  I think there is a way to change the pamusb configuration so that it will run scripts. I'm just not sure how to integrate this with truecrypt.  I have the folder set up so that I have to have the usb drive plugged in to decrypt by using a key file. 

I guess my first question is how do I get pamusb to run scripts and how to I use a script to automate truecrypt.

I do understand that this is less secure that doing it by hand but I will eventually switch to a small memory card like the one in my phone.  That way it is separate from the thumb drive needed to log in.

My second problem I'm running into is encrypting home post-installation.  Is it possible or do I need to just create another user and move everything over?

---

### Post by iceman_ch on 2010-07-29
One other problem I'm having.  Now that I've set the USB to being required every time I use sudo it asks for both.  I want it to ask for either with the preference being the USB stick and the password as fall back.  I've been messing around with the Pam config files and reading a ton about pam online but, I'm not getting the answers I need.  What I need to know is where to place the line requiring the USB key so that login uses it.  I don't think that common-auth will work as sudo is using this to.  I tried placing it into login but, that didn't work.  I'm wondering if I just create another file called something like Common-USB and then have login include it.


I also believe I found the part of the solution to mounting truecrypt volumes automatically.  Apparently PAM will do this by using pamexec.  I'll try this after I find the command line for mounting true crypt volumes.

---

### Post by espressobeanie on 2010-07-29
I don't know of any packages that offer support for USB fingerprint reader or USB thumbdrive keys. I know you're trying to turn a USB thumb drive into a bootable smart card for secure login authentications, but no software that I'm aware of on Ubuntu will do this.

The PAM module, I believe, starts up after login and you want to have it execute as part of the login. Look at libpam-p11.

---

### Post by iceman_ch on 2010-07-29
> **espressobeanie said:**
> I don't know of any packages that offer support for USB fingerprint reader or USB thumbdrive keys. I know you're trying to turn a USB thumb drive into a bootable smart card for secure login authentications, but no software that I'm aware of on Ubuntu will do this.

The PAM module, I believe, starts up after login and you want to have it execute as part of the login. Look at libpam-p11.


I've actually got that part working just not exactally the way I want it to.  I've downloaded and installed pamusb.  This allows  pam to authenticate using a usb drive. It looks at the vendor, model, and S/N of the drive to verify that it is the correct one.  So right now when I turn on my computer it ask for a password.  I enter the password and it says it is incorrect.  When I plug in the USB drive and then type the password the system lets me in.  When I first installed pamusb I wanted to make sure everything was working before I locked myself out so I had set the pamusb module set to optional in the common-auth.  What this did is when I wanted to sudo as long as I had the usb drive plugged in it wouldn't ask for a password.  If I unplugged the drive then it would ask for a password.  When I started the computer just plugging in the drive was enough to let me login without using a password.  After changing common-auth so that the drive was required I now have to have the drive plugged in and the password typed to login or sudo. I'd like to change that do that sudo only requires a password when the drive is not plugged in.

As far as stealing my info from the Internet...... Well this is ubuntu good luck. j/k I don't have any servers running.  I also have a firewall despite not having any servers.  Eventually I will get HID running but that is farther down the road.  Also,  that would be the point of encrypting the home folder, swap and .... I'm not sure what else.

---

### Post by stlsaint on 2010-07-29
From your plans it seems you are interested in security but i must warn of the use of a USB as your access to your system. Should that USB get lost or broken or fails you are in for a world of hurt. Especially with you wanting to encrypt your /home. With that said i would suggest you create a seperate /home partition and checkout [TrueCrypt.]("http://www.truecrypt.org/")

---

### Post by iceman_ch on 2010-07-29
I agree that losing the thumbdrive would suck.  Thats why I'm planning on enabling three thumbdrives.  One in the safe, one on me and one hidden away.  

From everything I've seen Ubuntu is very secure to outside intruders but, what about people who have physical access to it.  This is why I'm trying to do what I'm doing.  Here's the problem anyone who knows nothing about Linux will be thwarted by all of this.  Anyone who uses linux regularly will know how to get around the physical security pretty easily.  Even after I set everything up it would take me minutes to gain root and unlock the account.  Thats why encryption with ecryptfs will be neccesary.  It is already set so that if you change the account password you have to know the old password to unlock the crypt.  So I guess the question is at what point is all of these plans just a nuisance to the end-user? Here is some questions that I have.

First I like truecrypt I'm already using it.  How can I script it or, does anyone have a place I can start reading on how to script it? I've searched everywhere for something and come up with nothing or really outdated material.

Second,  all of these plans are good and all but like I said it would take minutes to gain root and change the password along with the auth files.  How can I secure the root gained through grub?  I don't necessarily want to get rid of it since I've used it twice already but, I don't see how you can truly secure a system to physical attacks without doing it.

---

### Post by iceman_ch on 2010-07-29
One other thing to think about.  It seems windows is far more secure as far as physical access.  Is this really the case? In all of the time that I've used windows I've never been able to recover lost passwords.  Well at least since XP anyways.  With Ubuntu it's relatively easy to gain access when you are physically there.  I will admit however that Linux is a million times more secure as far as none physical attacks.


By the way I've been using linux for just about everything for at least the last two years and I love it.  So I'm not knocking on linux it's just a thought.

---

### Post by HPD2 on 2010-07-30
Windows is **_NOT_** more secure in regards to physical access. Physical access is the weak link in computer security. There are cd's out there that you can boot and reset or crack a windows password, or you could remove the drive then add it as a secondary to a linux system and have full access to it. If a malicious user has physical access to a machine the fight is already lost.

---

### Post by fargle on 2010-07-30
> **HPD2 said:**
> Windows is **_NOT_** more secure in regards to physical access. Physical access is the weak link in computer security. 

[...]

If a malicious user has physical access to a machine the fight is already lost.

Especially with Windows.  I have a nifty little tool that will completely unlock the ctrl-alt-delete screen lock on any Windows machine with a Firewire port.  You can't shut it off under Windows at all.

It will also dump the entire contents of RAM of any running Windows machine, trivial to find unencrypted goodies in that dump.

As for scripting Truecrypt, I believe it has command-line options, I have a couple of bash aliases that let me mount some Truecrypt partitions manually when I want them, but leave them unmounted when I don't need them.

And for auto-mounting encrypted drives/partitions on login (but unfortunately, I don't think still on logout!), use the package libpam-mount.  You put the partitions in /etc/security/pam_mount.conf.xml.

Otherwise nothing to add!  ;)

---

### Post by cprofitt on 2010-07-30
> **HPD2 said:**
> Windows is **_NOT_** more secure in regards to physical access. Physical access is the weak link in computer security. There are cd's out there that you can boot and reset or crack a windows password, or you could remove the drive then add it as a secondary to a linux system and have full access to it. If a malicious user has physical access to a machine the fight is already lost.

The same could be done against a Linux machine.

On Windows though I can use a TPM module and bit-locker to encrypt the drive making it near impossible (according to the marketing) to remove the HD and access the data. If you encrypt the drive w/o the password booting with a password cracking CD will not help either.

---

### Post by HPD2 on 2010-07-31
> **cprofitt said:**
> The same could be done against a Linux machine.

On Windows though I can use a TPM module and bit-locker to encrypt the drive making it near impossible (according to the marketing) to remove the HD and access the data. If you encrypt the drive w/o the password booting with a password cracking CD will not help either.

I'm not saying a similar attack couldn't be levied against a Linux machine.

Even if a computer is secured with bit-locker a user can obtain the password through a cold boot attack.

[Here is some info on a cold boot attack.]("http://en.wikipedia.org/wiki/Cold_boot_attack")

---

### Post by iceman_ch on 2010-08-01
Well I've got the blue tooth proximity working.  It was amazingly easy.  I'm still looking for a good tutorial to use Fprint and get the fingerprint reader working. The USB thumb drive/key is also working....well mostly.  It works great for login but, I don't want to have to use a password every time I sudo if I have the key inserted. I'm still looking for documentation on the inner workings of pam but, I'm not coming up with a whole lot.  Mostly outdated stuff.  I did find some great tutorials on scripting truecrypt and using pam to accomplish that.  I'm sure in a couple of days I'll have that working.  So everything is coming together slowly.  One thing I haven't been able to find yet (mostly because I haven't googled it yet) but, does anyone know where a good tutorial is for securing root so that you can't just have grub drop you into root when ever you feel like.  I'm not sure if I'll implement it or not I guess it all depends of if I get the encryption of home done or not.

---

### Post by iceman_ch on 2010-08-01
> **HPD2 said:**
> Windows is **_NOT_** more secure in regards to physical access. Physical access is the weak link in computer security. There are cd's out there that you can boot and reset or crack a windows password, or you could remove the drive then add it as a secondary to a linux system and have full access to it. If a malicious user has physical access to a machine the fight is already lost.



I agree that every systems weaknes is physical access. I guess the ultimate computer as far as security would be one that you don't have physical access to.  This would probably be very inconvenient.  

I still think linux is easier to get into then windows.  Anyone who loses a password and does a google search on password recovery in linux would within ten minutes be able to reset the password with out any special tools.  Where as in windows while not completely secure is still harder to get to.  You have to have a tool or create a tool in order to accomplish it.  I can get into linux without opening the case,  In my opinion that makes windows more secure as far as physical access and login.  Everything else linux wins in.

---

### Post by HPD2 on 2010-08-02
> **iceman_ch said:**
> I agree that every systems weaknes is physical access. I guess the ultimate computer as far as security would be one that you don't have physical access to.  This would probably be very inconvenient.  

I still think linux is easier to get into then windows.  Anyone who loses a password and does a google search on password recovery in linux would within ten minutes be able to reset the password with out any special tools.  Where as in windows while not completely secure is still harder to get to.  You have to have a tool or create a tool in order to accomplish it.  I can get into linux without opening the case,  In my opinion that makes windows more secure as far as physical access and login.  Everything else linux wins in. 

I'm not saying Linux is any better, but im saying that Windows is not more secure. Both have ways to change, bypass, or remove a password. Some one who knows what there doing will get in with physical access.

For both Linux and Windows if you were to boot off a live cd and mount the target drive you wouldn't need to worry about passwords.

---

### Post by iceman_ch on 2010-08-03
Ok, well I'm getting closer.  It seems every time I get one problem solved another one pops up.  I've got the scripts working with the usb drive.  When I unplug the usb drive it will run the scripts under sudo without asking for a password.  So now I need to figure out how to lock the scripts down really well so that they can't be messed with.  The other problem I'm having is that now when I pull out the usb stick the screen locks but as soon as I wiggle the mouse it unlocks.  After a couple of seconds of the bluetooth being disconnected the screen locks and requires a password to get back in.  I think that the blueproximity program is causing the problem.  If I type in 

gnome-screensaver-command --lock

in the command line it does the same thing

Here are the scripts so far.

**usb_unlock.sh**

gnome-screensaver-command --deactivate
sleep 5
sudo hciconfig hci0 up

**usb_lock.sh**

#!/bin/bash

gnome-screensaver-command --lock
sleep 5
sudo hciconfig hci0 down


**pamusb.conf**
<?xml version="1.0" ?><!--
pamusb.conf: Configuration file for pam_usb.

See [http://www.pamusb.org/doc/configuring](http://www.pamusb.org/doc/configuring)
--><configuration>
	<!-- Default options -->
	<defaults>
		<!-- Example:
			<option name="debug">true</option>
		-->
	</defaults>

	<!-- Device settings -->
	<devices>
		<!-- Example:
		Note: You should use pamusb-conf to add devices automatically.
		<device id="MyDevice">
			<vendor>SanDisk Corp.</vendor>
			<model>Cruzer Titanium</model>
			<serial>SNDKXXXXXXXXXXXXXXXX</serial>
			<volume_uuid>6F6B-42FC</volume_uuid>
			<option name="probe_timeout">10</option>
		</device>
		-->
	<device id="MyKey">
	<vendor>
		
	</vendor>
	<model>
		
	</model>
	<serial>
		
	</serial>
	<volume_uuid>
		
	</volume_uuid>
</device></devices>


	<!-- User settings -->
<users>
		<!-- Note: Use pamusb-conf to add a user, then you can tweak
		 	manually the configuration here if needed.
		-->

		<!-- Example:
			Authenticate user scox using "MyDevice", and configure pamusb-agent
			to automatically start/stop gnome-screensaver on key insertion and
			removal:
			<user id="scox">
				<device>MyDevice</device>
				<option name="quiet">true</option>
				<agent event="lock">gnome-screensaver-command -lock</agent>
				<agent event="unlock">gnome-screensaver-command -deactivate</agent>
			</user>

			Configure user root to authenticate using MyDevice, but update one
			time pads at every login (default is 1 hour):
			<user id="root">
				<device>MyDevice</device>
				<option name="pad_expiration">0</option>
			</user>
		-->
	<user id="chris">
		<device>MyKey</device>
		<option name="quiet">true</option>
		<agent event="lock">sudo /etc/scripts/usb_lock.sh</agent>
		<agent event="unlock">sudo /etc/scripts/usb_unlock.sh</agent>
	</user>
</users>

	<!-- Services settings (e.g. gdm, su, sudo...) -->
	<services>
		<!-- Example: Speed up hotplugging by disabling one time pads -->
		<!--
		<service id="pamusb-agent">
			<option name="one_time_pad">false</option>
		</service>
		-->

		<!-- Disable output for 'su' (needed for gksu) -->
		<!--
		<service id="su">
			<option name="quiet">true</option>
		</service>
		-->
	</services>
</configuration>

---

### Post by JFollest on 2011-03-08
This sounds perfect for what I need. Will this work on a desktop setup also?

Can you give more details on how to set this up and run it, I'm fairly new to Linux but can get around it well. 

Thanks
Joe

---

