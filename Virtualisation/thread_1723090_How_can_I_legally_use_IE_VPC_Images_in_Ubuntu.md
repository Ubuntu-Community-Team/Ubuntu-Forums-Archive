---
title: "How can I legally use IE VPC Images in Ubuntu?"
date: 2011-04-06
forum: Virtualisation
---

### Post by twopointfour on 2011-04-06
I'm a web developer and I need to be able to test my websites in IE6, IE7, IE8, and IE9. Since Microsoft is stupid, you can't install more than one version of Internet Explorer in Windows at a time.

I have a single legal copy of Windows 7 (which can't even run IE6 or IE7) that I'm running in VirtualBox. Right now IE9 is installed, and I should keep it that way because IE9 doesn't run in Windows XP. So I need to find a way to run IE6, IE7, and IE8, without pirating anything.

In order to help web developers with this IE testing problem, Microsoft has released some Virtual PC images of Windows XP SP3 with IE6, IE7, and IE8 installed: [https://www.microsoft.com/downloads/en/details.aspx?FamilyID=21eabb90-958f-4b64-b5f1-73d0a413c8ef&displaylang=en](https://www.microsoft.com/downloads/en/details.aspx?FamilyID=21eabb90-958f-4b64-b5f1-73d0a413c8ef&displaylang=en)

To make it simple, I'll just talk about trying to get the WinXP SP3 IE6 virtual machine working.

I downloaded XPSP3-IE6.EXE, and extracted it's contents:

```
cabextract XPSP3-IE6.EXE
```This extracted IE6Compat.vhd and some txt files. VHD files are Virtual PC hard drive images. I then converted the IE6Compat.vhd to a raw binary with qemu-img:

```
qemu-img convert IE6Compat.vhd -O raw IE6Compat.bin
```Then I used VirtualBox's VBoxManage to turn the raw binary disk image into a VirtualBox disk image:

```
VBoxManage convertfromraw IE6Compat.bin IE6Compat.vdi
```Then I created a new Windows XP VM in VirtualBox and used this vdi file as it's hard drive and booted. It sort of worked!

It gave me an error saying that my since my hardware has changed a lot (Virtual PC hardware is significantly different than VirtualBox hardware, apparently) that Windows XP is no longer activated and I have 3 days to activate it again. Also, at this point the network drivers weren't installed so I had no internet access. It also gave tons of error messages and "Found new hardware" windows that I ignored, but it logged me in the first time. I was able to install Guest Additions and reboot.

After rebooting, it brought me to the user selection screen. When I choose "IE User" it gives an error saying I'm not allowed to login until I activate Windows XP. When I try activating, it wants an activation key, which obviously I don't have. This is where I'm stuck. It doesn't seem like it's possible to use Microsoft's Virtual PC images in VirtualBox because of activation issues.

I also tried installing Virtual PC in my Windows 7 VM. It wouldn't work though because it says it can only run it on hardware that supports virtualization, and clearly my VirtualBox VM hardware doesn't support that.

I'm at a loss. How am I supposed to legally test IE6, IE7, IE8, and IE9 from Ubuntu when I only have a single license of Windows 7?

---

### Post by tgm4883 on 2011-04-06
> **twopointfour said:**
> I'm a web developer and I need to be able to test my websites in IE6, IE7, IE8, and IE9. Since Microsoft is stupid, you can't install more than one version of Internet Explorer in Windows at a time.

I have a single legal copy of Windows 7 (which can't even run IE6 or IE7) that I'm running in VirtualBox. Right now IE9 is installed, and I should keep it that way because IE9 doesn't run in Windows XP. So I need to find a way to run IE6, IE7, and IE8, without pirating anything.

In order to help web developers with this IE testing problem, Microsoft has released some Virtual PC images of Windows XP SP3 with IE6, IE7, and IE8 installed: [https://www.microsoft.com/downloads/en/details.aspx?FamilyID=21eabb90-958f-4b64-b5f1-73d0a413c8ef&displaylang=en](https://www.microsoft.com/downloads/en/details.aspx?FamilyID=21eabb90-958f-4b64-b5f1-73d0a413c8ef&displaylang=en)

To make it simple, I'll just talk about trying to get the WinXP SP3 IE6 virtual machine working.

I downloaded XPSP3-IE6.EXE, and extracted it's contents:

```
cabextract XPSP3-IE6.EXE
```This extracted IE6Compat.vhd and some txt files. VHD files are Virtual PC hard drive images. I then converted the IE6Compat.vhd to a raw binary with qemu-img:

```
qemu-img convert IE6Compat.vhd -O raw IE6Compat.bin
```Then I used VirtualBox's VBoxManage to turn the raw binary disk image into a VirtualBox disk image:

```
VBoxManage convertfromraw IE6Compat.bin IE6Compat.vdi
```Then I created a new Windows XP VM in VirtualBox and used this vdi file as it's hard drive and booted. It sort of worked!

It gave me an error saying that my since my hardware has changed a lot (Virtual PC hardware is significantly different than VirtualBox hardware, apparently) that Windows XP is no longer activated and I have 3 days to activate it again. Also, at this point the network drivers weren't installed so I had no internet access. It also gave tons of error messages and "Found new hardware" windows that I ignored, but it logged me in the first time. I was able to install Guest Additions and reboot.

After rebooting, it brought me to the user selection screen. When I choose "IE User" it gives an error saying I'm not allowed to login until I activate Windows XP. When I try activating, it wants an activation key, which obviously I don't have. This is where I'm stuck. It doesn't seem like it's possible to use Microsoft's Virtual PC images in VirtualBox because of activation issues.

I also tried installing Virtual PC in my Windows 7 VM. It wouldn't work though because it says it can only run it on hardware that supports virtualization, and clearly my VirtualBox VM hardware doesn't support that.

I'm at a loss. How am I supposed to legally test IE6, IE7, IE8, and IE9 from Ubuntu when I only have a single license of Windows 7?

Hmm tough spot, thanks Microsoft.

IIRC Windows 7 has an XP compatibility mode (which essentially is an XP VM inside Windows 7). Which that would likely be terrible for performance, you may be able to use that to test IE6

---

### Post by teeks99 on 2011-04-07
I think its possible to install multiple versions of IE under WINE...

I believe if you use winetricks, it goes out to the MS website and downloads the installer for you and runs it....which I believe qualifies as not pirating anything.

---

### Post by twopointfour on 2011-04-08
Oh, I hadn't thought of doing this in Wine. In any case, it turns out that this program works alright: [http://www.my-debugbar.com/wiki/IETester/HomePage](http://www.my-debugbar.com/wiki/IETester/HomePage)

It runs in the Windows 7 VM and it lets you open up tabs for different versions of IE.

---

### Post by SeijiSensei on 2011-04-08
As a professional, you might consider investing in a [Technet subscription]("http://technet.microsoft.com/en-us/subscriptions/buy.aspx").  $199 will buy you access to fully-licensed versions of just about every MS product available except Enterprise ones.  That includes older products like XP and Office97 as well as Win7 and Office 2010. You can also download additional license keys (number varies) to create multiple installations of a single product like XP Professional.

---

### Post by highspider on 2011-04-15
Here how I test my site for IE compatibility with Ubuntu. 
 (a lot less work then a whole virtual machine)

install the back dated wine version 1.0 (needed for ies4linux to compile)
```

sudo apt-get install wine1.0

```install ies for linux
```

wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
tar zxvf ies4linux-latest.tar.gz
cd ies4linux-*
./ies4linux --no-gui

```NOTE: you can install IE1, 1.5, 2, 5, 5,5 and beta 7 also see "./ies4linux --full-help" for info

Now that IE's are installed ~ update to the newest wine
```

sudo apt-get install wine

```at the time wrote this the newest wine in repos was 1.2 aka sudo apt-get install wine1.2

to run or not run "files are default to /home/<USERNAME>/bin/"
```

/home/$USER/bin/<ie#>
[COLOR=Lime]ergo for me to load ie6[/COLOR]
/home/$USER/bin/ie6
[COLOR=Lime]or [/COLOR]
cd ~/bin  
./<ie#>

```Yeah some times it crashes but I only really use to test a site. I wouldn't recommend non-stop surfing with it.
if you get stuck just use (it not perfect but I like it)
```
killall -9 wineserver
```



For me i don't care about any other IE except 6 because basicly, it suck's above all others.   A perfect CSS (aka width height area of web page) will look fine with firefox, seamonkey, G-chrome, safari, IE5, IE7, IEwhatever and look like crap with IE6 so oods are to test to IE6 and it will look good on every thing else.

---

### Post by 4levels on 2011-04-20
Hi all,

I had the same issue using VirtualBox and the downloaded VPC images from Microsoft.  I was able to overcome it this way:
The first time you start your virtualbox machine, before installing the guest additions, windows is asking for some system files (battc.sys and so on)  I googled and downloaded these, created an iso image from it with Brasero and mounted that in Virtualbox.  The most important one is ofcourse the one for your network card to be able to activate online: pcntpci5.sys.  Once you've installed that one, your network card should be working and you're able to activate windows..

You can now go ahead, install the guest additions and reboot.  Windows will activate online ;-)

Hope this get's you going as well!

Cheers

PS. Virtualbox also supports MS's VHD images, so no need to qemu the images into another format ;-)

---

### Post by lazypoet on 2011-06-28
I had the same activation issue with the new versions of the IE VPC image. However, if you choose to **activate over the phone**, call the number, and go through the steps, it **will** activate.

I thought this was important enough information that I should bump the thread, considering it was on the first page of a Google search about using IE VPCs in Ubuntu.

---

### Post by Gregsen on 2011-07-17
Hiho,

dunno if this thread is still active...i have posted a small tutorial on this topic at [google+]("https://plus.google.com/102594491399954540976/posts"). Basically, once it asks for activation, reboot, hit F8  during boot up, boot in "safe mode" and become administrator (password is "Password1"). Now you can copy your drivers running ```
D:\VBoxWindowsAdditions-x86.exe /extract /D=C:\Drivers
``` (that is, having installed guest additions before), get your ethernet adapter working and activate yo precious Windows.

My tutorial at G+ is just an updatet version from [zytzagoo.net]("http://zytzagoo.net/blog/2009/03/20/howto-running-ie6-ie7-and-ie8-on-ubuntu-intrepid-810-using-virtualbox/")

Gregsen

---

### Post by nrogers64 on 2012-04-18
Here's how I got it working:

I ignored all of Windows' prompts to install drivers and then I installed VirtualBox Guest Additions and rebooted. After that, I dealt with all of Windows' prompts to install drivers. In order to do that, I mounted an ISO with these twelve files:

[LIST=1]
[*]ac97intc.sys
[*]battc.sys
[*]cmbatt.sys
[*]compbatt.sys
[*]hidclass.sys
[*]hidparse.sys
[*]hidusb.sys
[*]mouhid.sys
[*]pcntpci5.sys
[*]usbohci.sys
[*]usbport.sys
[*]usbui.dll
[/LIST]

After that, I was able to activate Windows over the Internet and Windows no longer prompted me to install drivers.

---

