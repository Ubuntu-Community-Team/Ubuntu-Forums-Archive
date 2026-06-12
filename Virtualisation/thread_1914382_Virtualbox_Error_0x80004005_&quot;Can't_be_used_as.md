---
title: "Virtualbox Error 0x80004005 &quot;Can't be used as the requested device type&quot;"
date: 2012-01-24
forum: Virtualisation
---

### Post by zcacogp on 2012-01-24
Chaps, 

I installed Virtualbox last week, as my wife needs to occasionally use WinXP, and Virtualbox seemed the best way of doing it. It worked fine, although the machine I created in it was only available to me - not to my wife. The machine runs XP Pro (from a legit installation disk and code I have from a previous computer I built), with Office and a couple of other things. 

I have now tried to make it available to both of us, and have broken it. I have the file which is the virtual machine ("WinXP.vdi"), and tried to put it in a commonly-accessible place, and then create 'new' VM's in VirtualBox with this file, but every time I try to create a machine in this way I am given the following error screen: 

[IMG]http://i76.photobucket.com/albums/j14/zcacogp/Screenshot-VirtualBox-Error.png[/IMG]

The error is listed as "The medium <filename> can't be used as the requested device type", and the result code is "NS_ERROR_FAILURE (0x80004005)".

I have tried replacing the *.vdi file in the same location it was originally in (~/home/ogp/VirtualBox VMs) and it has made no difference - the same error is present. 

I've googled this, and it seems that there are a number of threads about it but none of the solutions listed work. Some more details: 

- I cannot make this work for either user now, although both users are in the group "vboxusers" (number 125, if it's relevant). 
- The *.vdi file has permissions drwxr-xr-x (listing the file gives 'drwxr-xr-x 4 root root 4096 2012-01-24 09:54 WinXP') 
- Renaming (or removing) the .virtualbox folder in my home directory makes no difference
- Running ```
sudo /etc/init.d/vboxdrv setup
```tells me that "sudo: /etc/init.d/vboxdrv: command not found"
- I have the latest version of dkms installed. 

I am sure I can wipe the *.vdi file and start from scratch, but I'd rather avoid this if I can. (I'm also guessing that, if/when I upgrade my version of Ubuntu, it would be a lot easier to keep the *.vdi file and therefore not have to re-build the virtual machine from scratch in the new installation, which is effectively what I am trying to do!) 

I'm running Ubuntu 11.04, and VirtualBox 4.0.4_OSE r70112. 

(I've put this thread in 'virtualisation' as it seems the most appropriate place for it. Mods, please do move it if it would do better elsewhere.) 

Thanks in advance for any help you can offer. 


Oli.

---

### Post by zcacogp on 2012-01-26
Not wanting to be cheeky or impatient ... but bump!


Oli.

---

### Post by zcacogp on 2012-01-28
Anyone? I can't be the first person to have had this problem, surely? 


Oli.

---

### Post by sulyi on 2012-01-29
I get same error here, trying to virtualize one of my disk. Though shared driver works fine. I've found data about accessing vboxsvr from other than net share.

---

### Post by sulyi on 2012-01-29
I've made some workaround with my stuff, and i got some variety of errors.
Finally i got exactly the same as yours. 

> **zcacogp said:**
> 
- The *.vdi file has permissions drwxr-xr-x (listing the file gives 'drwxr-xr-x 4 root root 4096 2012-01-24 09:54 WinXP') 


And i am most certain that you should change at least the group  ownership of the file to vboxusers and give 660 (-rw-rw--- ) permission  to it.  I do not know about the parent directory, but if that's owner is  root then vboxusers are effected as other user, so the third, last part  of permission settings. Maybe you should conceder chancing the  ownership of the parent too.

---

### Post by joelson854 on 2012-03-03
Hi friend, i have the same error, and i find a way to add .vmdk file created by comand createrawvmd to virtualbox ide controler... but im not know how make this in user normal.

i start virtualbox with sudo (sudo virtualbox) and virtualbox open without vms created... and i create a vm for test and i susesfull add .vmdk to vbox.

and i can boot from my usb pen 100% :)

the problem stay in permissions with vboxmanage i think.

but im not know how apply permissions to vboxmanage or vbox to got full acess to usb with my user normal. 
remember.. all my usb work 100% in situation normal. im only have problens with RAW disk.

i hope helped you, and sorry by my bad english, im brazilian.

---

### Post by joelson854 on 2012-03-03
> **joelson854 said:**
> Hi friend, i have the same error, and i find a way to add .vmdk file created by comand createrawvmd to virtualbox ide controler... but im not know how make this in user normal.

i start virtualbox with sudo (sudo virtualbox) and virtualbox open without vms created... and i create a vm for test and i susesfull add .vmdk to vbox.

and i can boot from my usb pen 100% :)

the problem stay in permissions with vboxmanage i think.

but im not know how apply permissions to vboxmanage or vbox to got full acess to usb with my user normal. 
remember.. all my usb work 100% in situation normal. im only have problens with RAW disk.

i hope helped you, and sorry by my bad english, im brazilian.
Hi again, i find a "Pig way" to add Raw disk to virtualbox.

i make the folowed up , and i create a vm in sudo virtualbox with the RAW pendrive, and use EXPORT APPLIANCE, save in you user folder, later chance permission with chmod and close you sudo virtualbox,, open you virtualbox normal and IMPORT APPLIANCE. and u will have a machine with disk RAW.

---

### Post by sulyi on 2012-03-07
It's been a while, but as I recall , it was 

VBoxManage internalcommands createrawvmdk

I had to play with uuid and stuff then gave disk privilege to vbox-users and off it went. Not very nicely, but I do not have too much rocket fuel in my ironclad.

Though, one of my friend told me he's vm boot over 5 min or something. He was blaming his cpu architecture, like there is no support on his comp for virtualization.

There can be truth in that, different processors has different instruction set. 

Meanwhile I've found [this]("http://blog.mybox.ro/2010/11/03/how-to-use-a-raw-disk-image-file-in-virtualbox/"). It was great help for me back then.

I'd add that I had to do this way, I was running file system manipulation on the guest.
To share disk space to transfer data or something  installing VBoxGuestAdditions.iso is much easier and safer. That way u get a virtual smb server on the guest which can be targeted on a directory of the host.

---

### Post by Docmero on 2012-05-16
I had this exact same error , and I solved it by simply mounting the partition where I put the virtual machine !!
So , Every time I should mount all my partitions before starting the virtual system !!  Can I make the ubuntu to mount all partitions automatically as system start up ?

---

### Post by mc1100 on 2012-08-23
Add yourself to the disk and vboxusers groups.

```
sudo usermod -a -G disk,vboxusers yourlogin
```

Then logout/login for the changes to take effect.

Hope that helps.

Martin

---

### Post by jibawakee on 2012-08-25
thanks the command above solved that for me ):P

---

