---
title: "Disable USB Storage Access On Ubuntu Linux"
date: 2014-08-06
forum: Security
---

### Post by malik3 on 2014-08-06
To** disable USB Storage Access on Ubuntu Linux**, I do the following:
Go to Terminal and on the command prompt, type
 sudo gedit /etc/modprobe.d/blacklist.conf
Then I enter the password when asked.  Next, go all the way to the  bottom of the file and add a lines below it.  The line with a “#” is for  documentation purposes and makes it readable to your audience.

 # disable usb storage access 
blacklist usb_storage Save the file and restart the computer.
its work very well but if i conect usb and then restart the after restart usb auto mount if i restart with out pluging usb then after restart i plug the usb it never mount.
Means if i restart computer with out pluging usb and after restart then i plug the usb it never mount but.............
if i plug usb and then resart pc then after restart the usb auto mount its never disabled

I am using ubuntu 14.04

---

### Post by sudodus on 2014-08-06
Welcome to the Ubuntu Forums :-)

I don't know why you want to disable USB storage access, and how much you want to be available in Ubuntu. Is the guest session without USB what you want?

If you want a secure system, that cannot read USB, that can actually *only* run the web browser, you can use a kiosk operating system, for example ***Webconverger***.

See also this link [https://help.ubuntu.com/community/FirefoxKiosk](https://help.ubuntu.com/community/FirefoxKiosk) and browse the internet for ***linux kiosk*** or ***ubuntu kiosk***

---

### Post by malik3 on 2014-08-06
Thanx for reply sudodus

I want to disable mass storage like usb cd rom is there any way. i want to restrict my pc to copy data if some one know my user password

---

### Post by sudodus on 2014-08-06
If a person has a fair knowledge of linux, it is enough to have physical access to the computer (to be in the same room) to be able to get all your data, unless you have encrypted home or encrypted disk. Without that knowledge a person will be stopped by a good (and secret) password.

You should not tell your password to anybody. If someone knows now, you should change your password.

Instead you can have separate user accounts for family members, friends etc. And these accounts should be regular user accounts without permission to run sudo. This prevents them from destroying the system by mistake and from reading files, that other users want to keep privately. A temporary user can also run the guest user account, which cannot store data in the computer. When the guest user logs out, its user data will be removed.

I think it makes no big difference for the security if USB and CD/DVD has read or write access.

-o-

If you want high security, use encrypted home and/or encrypted disk. I think it is enough with encrypted home (actually no encryption at all for most people). But you are on your own. If you forget the password, you lose your data. So you had better remember the password or store it in a bank vault or similar.

---

### Post by malik3 on 2014-08-07
[**[COLOR=#C61919][B]sudodus**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1499021") Thanx for kind reply 
Sir i have full disk encrypted and also home folder encrypted but when pc is on there is no advantage of encryption so if any one know how i can disable Mass Storage plz tell me.

---

### Post by sudodus on 2014-08-07
In order to have high security, shut the machine off, when you are not using it.

If you have a reasonably good password and lock the computer, it will not be available for people without special skill. They will not be able to log into your user. They might insert a CD/DVD/USB drive and boot from there, but they will find an encrypted internal drive.

---

### Post by colin_wills on 2015-03-20
I disabled storage USBs on an xubuntu 14.04 machine as Administrator user called admin by:

  [FONT=courier new]**mv /lib/modules/$(uname -r)/kernel/drivers/usb/storage/usb-storage.ko /home/admin/**[/FONT]

  In **[FONT=courier new]/etc/rc.local[/FONT]** add:

      [FONT=courier new][B]rmmod uas
      rmmod usb_storage[/B][/FONT]

  Reboot.  Now ordinary Desktop users *should* have no way to connect USB storage devices.  This can be useful e.g. eliminate risk of data exfiltration or malware propagation via USB storage devices.  Pity there is no user group to control this.

---

### Post by HermanAB on 2015-03-21
It all depends on the threat level.  If you wish to protect your system against your little 5 year old kid sister, then disabling USB may help - against anyone else, not so much, since anyone else may either re-enable USB, or copy the data using hundreds of other methods.

---

