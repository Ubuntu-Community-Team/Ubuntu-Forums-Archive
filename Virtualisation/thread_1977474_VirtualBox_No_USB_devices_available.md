---
title: "VirtualBox: No USB devices available"
date: 2012-05-10
forum: Virtualisation
---

### Post by ct2034 on 2012-05-10
Hi, 
I am running Ubuntu 12.04 with VirtualBox and a Windows 7x64 as guest. But I can't mount any USB devices, they are all greyed out. I used to work, but now it doesn't. I tried already several things:

This is NOT a problem of vboxusers group! I am in this group:
```
ch@ch-laptop:~$ id
uid=1000(ch) gid=1000(ch) groups=1000(ch),4(adm),20(dialout),24(cdrom),46(plugdev),105(lpadmin),119(admin),122(sambashare),127(vboxusers)

```Another solution i tired is this one: 
> Edit /etc/fstab and add:

```
none /proc/bus/usb usbfs devgid=XXX,devmode=664 0 0
``` but I can't add the folder usb to bus, maybe because I'm using 12.04 ..


Please Help me, I tried everything!

---

### Post by Habitual on 2012-05-10
Guest Additions (re)installed?

---

### Post by ct2034 on 2012-05-10
> **Habitual said:**
> Guest Additions (re)installed?
Thanks 4ur suggestion. I have reinstalled it, but nothing changed. :(

---

### Post by westie457 on 2012-05-10
Did you install virtualbox from the repos or from here [https://www.virtualbox.org/](https://www.virtualbox.org/)

---

### Post by ct2034 on 2012-05-10
Another interesting aspect is: when I configure the VM, in the USB-filter list i can click on 'add filter from device' and see all the devices active. But the filters are not executed, as no devices are connected.. and i see the same devices in the menu of the running vm, where all are grayed out.

---

### Post by ct2034 on 2012-05-10
> **westie457 said:**
> Did you install virtualbox from the repos or from here [https://www.virtualbox.org/](https://www.virtualbox.org/)
I installed the *.deb from the website:
[http://download.virtualbox.org/virtualbox/4.1.14/virtualbox-4.1_4.1.14-77440~Ubuntu~precise_amd64.deb](http://download.virtualbox.org/virtualbox/4.1.14/virtualbox-4.1_4.1.14-77440~Ubuntu~precise_amd64.deb)

---

### Post by westie457 on 2012-05-10
Next question. Are the USB devices connected when you start the virtual machine?

If not connected at that time to access USB devices after boot up you need to go to the Devices menu of the running VM and select the USB device there.

One extra piece of advice here is **do not**select the mouse as this will lock the mouse into the VM window and is very hard to unlock.

---

### Post by ct2034 on 2012-05-10
> **westie457 said:**
> Next question. Are the USB devices connected when you start the virtual machine?

If not connected at that time to access USB devices after boot up you need to go to the Devices menu of the running VM and select the USB device there.

One extra piece of advice here is **do not**select the mouse as this will lock the mouse into the VM window and is very hard to unlock.
Yes, the devices are connected before starting. As I said, I can see them in the menu, but they are disabled. (gray)
And believe me: i would be so happy if the machine would lock my mouse receiver, but how should it do this with only gray entries?? ;)

---

### Post by westie457 on 2012-05-10
This might seem to be a strange question.
Is 12.04 your original installation of Ubuntu or did you upgrade from an earlier version?

The reason for asking is when I first started with OSE Virtualbox it was installed whilst using 10.10. When I upgraded to 11.04 and had to use an updated version of Virtualbox if I tried to install the version for 11.04 over the top of the earler version I too lost access to USB devices and a few other things.
The solution for me was to use the updated version for 10.10. Even now while using 11.10 I still have to use virtualbox updates for 10.10.

You might have to try the same if you started with an earlier version.

If however 12.04 is your first go I have to admit that I am stumped on offering a solution.

---

### Post by ct2034 on 2012-05-10
> **westie457 said:**
> This might seem to be a strange question.
Is 12.04 your original installation of Ubuntu or did you upgrade from an earlier version?

The reason for asking is when I first started with OSE Virtualbox it was installed whilst using 10.10. When I upgraded to 11.04 and had to use an updated version of Virtualbox if I tried to install the version for 11.04 over the top of the earler version I too lost access to USB devices and a few other things.
The solution for me was to use the updated version for 10.10. Even now while using 11.10 I still have to use virtualbox updates for 10.10.

You might have to try the same if you started with an earlier version.

If however 12.04 is your first go I have to admit that I am stumped on offering a solution.
Hey, this is by far no strange question, caue this is actually the case. i am using ubuntu only for about 2 months (again) but i had to update it all the way from 10.10 because of some other strange errors ... :-/
so, u sggest to install the virtualbox updates for 10.10? could this work? cause actually its a downgrade .. ?
But thanks for this idea.. i'll try this trmw. :)

---

### Post by westie457 on 2012-05-10
> **ct2034 said:**
> Hey, this is by far no strange question, caue this is actually the case. i am using ubuntu only for about 2 months (again) but i had to update it all the way from 10.10 because of some other strange errors ... :-/
so, u sggest to install the virtualbox updates for 10.10? could this work? cause actually its a downgrade .. ?
But thanks for this idea.. i'll try this trmw. :)

If you carried virtualbox through the upgrades from 10.10 whenever there is a vbox update you should be informed by VBOXs own update manager and it will -does- state the version you need. In this case the version for 10.10 (Maverick Meerkat). 

Good luck when you try it.

---

### Post by ct2034 on 2012-05-11
> **westie457 said:**
> If you carried virtualbox through the upgrades from 10.10 whenever there is a vbox update you should be informed by VBOXs own update manager and it will -does- state the version you need. In this case the version for 10.10 (Maverick Meerkat). 
Okay, I tried it. I installed the version for 10.10 from virtualbox.org - and USB works :D
But now i get strange error messages from packetmanagement about some dependencies which are not satisfied. and the internal update managment dont shows me new updates, it says it is up to date

---

### Post by westie457 on 2012-05-11
Hi I take it you installed this version - virtualbox-4.1_4.1.14-77440~Ubuntu~maverick_i386  which is the latest. Also did you upgrade the Guest Additions?

Can you post the output of the two common commands please ```
sudo apt-get update

sudo apt-get upgrade
```

I am curious about what the dependencies are.

Thank you

---

### Post by turbos4 on 2012-05-14
[B]ppa Oracle VM virtualbox

#sudo add-apt-repository "deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) [/B]precise contrib"

#wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -

#sudo apt-get update

#sudo apt-get install virtualbox-4.1

Download extension pack and install it.

And YOU have to add ur user to VBOXUSERS.

Are using Ubuntu 12.04LTS.

---

### Post by syncdram on 2012-05-14
I just posted a video how to...[http://www.youtube.com/watch?v=ThA9I07m_GA&list=UUB37B20bZabA4D9V-TZ7rig&index=1&feature=plcp](http://www.youtube.com/watch?v=ThA9I07m_GA&list=UUB37B20bZabA4D9V-TZ7rig&index=1&feature=plcp)  guest additions installed as well. Hope this helps.

---

### Post by shades3 on 2013-01-11
> **turbos4 said:**
> [B]ppa Oracle VM virtualbox

...[/B]

And YOU have to add ur user to VBOXUSERS.

...

This did it. Thanks!

---

### Post by johnaaronrose on 2013-09-11
I have a clean install of Precise 64 bit. I installed VirtualBox 4.1.12 from Ubuntu's repos, together with the Guest additions iso. I've 'added' Guest Additions using VirtualBox. I've also added the corresponding Extension Pack (i.e. version 4.1.12). I'm running Windows XP as the Guest. Everything works (e.g. shared folders, mouse integration) fine except for "no usb devices" both in the Devices>USB menu entry & the icon at the window's base. I have myself included as a user in the vboxusers group. Both the "Enable USB Controller" & "Enable USB 2.0 (EHCI) Controller" check boxes are set in VirtualBox's Settings>Storage. 

I'm baffled. Any ideas please?

---

### Post by JKyleOKC on 2013-09-13
> **johnaaronrose said:**
> I'm baffled. Any ideas please?Have you created any USB filters in the vbox "Settings" page where you enabled USB? You may need a single "empty" filter to let the guest system identify the host's ports; this should make the list of plugged-in devices available under the "Devices" menu, and checking one of them there should connect it to the guest system.

If you want the device to automatically connect to the guest, bypassing the host entirely, you need to create a specific filter for it by having it plugged in when you create the filter, and selecting that device as the filter's subject. Complete details are in the help file.

I have both situations set up on a number of VMs here, with both XP and Win2K guests, and all of them work as expected. Hope this helps!

---

### Post by johnaaronrose on 2013-09-15
I have tried creating an empty usb filter with usb stick plugged in but no go. I'm away from home for a week. Will try again when home.

---

### Post by johnaaronrose on 2013-09-23
Thanks, Jim. It worked OK provided that I had the memory stick plugged in when I added a filter & selected the appropriate device. 

PS after the hack of the forum, there is no automatic login when I click on the forum's bookmark. Also, the login procedure does not return me to the thread that I was looking at when I want to reply to a post . Is there a cure for these nuisances?

---

### Post by JKyleOKC on 2013-09-23
> **johnaaronrose said:**
> PS after the hack of the forum, there is no automatic login when I click on the forum's bookmark. Also, the login procedure does not return me to the thread that I was looking at when I want to reply to a post . Is there a cure for these nuisances?I've not yet found one, but here's how I deal with it:

You can go into your profile and find a link to your own "subscribed threads" list, and create a bookmark to that page. Mine is to hxxp://ubuntuforums.org/subscription.php (I mangled the front to keep from creating an actual link in this message) and yours should be the same since the php page won't do anything unless you are logged in.

When I click that bookmark, it takes me to the front-end login page, then redirects to the new login procedure. Eventually, though, I land on the forums' front page. At that point I click my "subs" bookmark again, and it takes me to my subscribed threads. When we reply to a post, we're automatically subscribed to it, so it's easy to carry on a conversation like this -- just takes five more mouse clicks and page loads than it did before.

If I find a message via a generic Google search and click on their link, it looks as if I go to the new login procedure instead of to the thread that the search found -- but appearances are deceiving. If I ignore the initial screen content and just scroll down, I find that I really am on the post that Google found for me. While I cannot reply to it, I can bookmark it, then log in and use that (temporary) bookmark to return to it just as I manage to reach my subscribed threads.

It's a pain, and the moderators said a month or more ago that ways would be found to make things work better, but I've not yet seen any. Perhaps forum staff may see this discussion and chime in...

---

