---
title: "no internet connection in guest(windows xp)"
date: 2012-09-13
forum: Virtualisation
---

### Post by iyasin on 2012-09-13
hi all,
i installed Windows XP as guest in VirtualBox and i do not have any internet connection.
my guest os (win xp) get me this message: Limit or no connectivity!

but when i installed Linux Mint or Ubuntu  as other guset i had internet connection !

does i install any package in host for use internet in win xp guest?
or have other solution?
what is problem?

thanks.

---

### Post by afz12 on 2012-09-13
Hi iyasin

I have several instances of XP running under Ubuntu 12.04 and previously under many earlier versions. I have never found any need to add anything for Internet connectivity - Firefox and Thunderbird work without any real effort - i.e. no need to change any Ubuntu settings or add extra software. I assume you have installed the guest additions - although these shouldn't affect Internet connectivity. (I also have mint cinnamon 32 and 64 bit running as you say, no problems, also mint mate 32 bit and soon 64 bit, all four under Virtualbox and working properly.

Are you operating through a proxy? If so you need to enter all the details in Network - if you have Synaptic, details need to be entered here also for proxy use. 

Other than that, I really don't know. Perhaps you can expand a bit on the particular version of XP you instantiate - I assume it's standard 32 bit desktop and works stand-alone (i.e. the file is not corrupted).

If you have any XP settings that you think may be applicable I can compare them with my XP machines and see if there is any difference.

---

### Post by iyasin on 2012-09-13
> **afz12 said:**
> Hi iyasin

I have several instances of XP running under Ubuntu 12.04 and previously under many earlier versions. I have never found any need to add anything for Internet connectivity - Firefox and Thunderbird work without any real effort - i.e. no need to change any Ubuntu settings or add extra software. I assume you have installed the guest additions - although these shouldn't affect Internet connectivity. (I also have mint cinnamon 32 and 64 bit running as you say, no problems, also mint mate 32 bit and soon 64 bit, all four under Virtualbox and working properly.

Are you operating through a proxy? If so you need to enter all the details in Network - if you have Synaptic, details need to be entered here also for proxy use. 

Other than that, I really don't know. Perhaps you can expand a bit on the particular version of XP you instantiate - I assume it's standard 32 bit desktop and works stand-alone (i.e. the file is not corrupted).

If you have any XP settings that you think may be applicable I can compare them with my XP machines and see if there is any difference.

thanks for your answer

i do not use any proxy.
yes it is 32 bit desktop and work stand-alone(version 5.1.2600),
it is extactly my ip config in guest when i enter **ipconfig** command:

```
Ethernet adapter Local Area Connection 2:
Connection-sepcific DNS suffix . :
Autoconfiguration IP Address . . . : 168.254.208.249
subnet Mask .:255.255.0.0
default Getway:
```

---

### Post by afz12 on 2012-09-13
HI iyasin

I wonder how you are connecting to the Internet, based on your script lines. I think usually the guest connects through Virtualbox to the host - in my case XP connects through to Ubuntu 12.04. This is automatic when you install Virtualbox and then the extension pack. After this you would have installed XP from a CD I suspect and this implies the Virtualbox connection to the host OS must be correct. Then it is a good idea to install the guest additions since the extension pack is installed. This is done inside XP. There is no need I've seen to ever write terminal code in Ubuntu. After XP is installed, and your PC or Notebook has an Internet connection, XP will use this because it "just sees" the Virtualbox network connection to the host. The host then connects to the Internet in an invisible manner, at least to XP. 

The only complication you may face is if you use an Ethernet cable from your PC etc for Internet access. If this plugs into the Ethernet port of a standard wireless modem, connected say to a landline (for initial access) then Internet connectivity should be automatic - at least I have always found this works without any setup (except a password!). However if you connect directly to another computer, by an Ethernet cable, then expect major problems. Windows computer to computer Ethernet is a mission - Windows - Linux is not much better. If this is your configuration, you need to set each computer up specifically. In windows it will require either "this computer connects directly to the Internet, other computers connect through this computer" OR "this computer connects to other computers...". Having done this before, it may take several reboots to get the link to work and even then it may not be stable.

Anyway I hope this is not your situation!

To continue, I have set up a Virtualbox VM for XP install and I have a spare XP CD for this. If you like, we could go through a step by step install, in parallel where I can start from a fresh CD - the same specifications as you report, 32 bit standard PC desktop etc and see what happens.

For this I suggest you check that you have the correct Virtualbox version. To be sure, I'd download a copy directly from the Virtualbox site along with the extension pack. I would be reluctant to try other measures. Virtualbox will install from the *iso download file using "software centre" as the install option. Then the extension pack will install using Virtualbox. I assume you have installed Virtualbox this way and haven't wound up with the OSE version.

Anyway, please advise on your preferred course of action iyasin

---

### Post by iyasin on 2012-09-13
yes maybe!
your guess mayeb is right about my problem.
in fact first i install Linux Mint(Cinnamon) on my pc...and i downloaded and installed VirtualBox as " **All distribution**" form VBox official site([https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)).

after that i have problem with Cinnamon and replace it with Ubuntu 12.4 LTS and install VBox(all distrobution) on it...VBox(all distribution) install on Ubuntu 12.4 with out any problem. 

maybe type of version of VBox that i use now cause this problem...
i am going replace this version of VBox to Ubuntu version of VBox.
i hope that your guess is being true.
thanks afz12.

---

### Post by SlugSlug on 2012-09-13
Change network settings in VB for your XP image

something like 'attach to physical network'

---

### Post by iyasin on 2012-09-13
> **SlugSlug said:**
> Change network settings in VB for your XP image

something like 'attach to physical network'

thanks a lot...
i am new....plz explaint it...i dont understand full...sorry

---

### Post by afz12 on 2012-09-13
Hi iyasin

I am installing a version of XP on Virtualbox at the moment. I thought I'd try it on Mint cinnamon, out of interest. So far its seems OK, but the installation has a definite step where it asks about "install network settings..." This needs to be clicked - perhaps you clicked the other box (2 options during XP install).

I'm using the 12.04 version of Virtualbox running on Mint cinnamon 64 bit for this experiment. However, if you use Ubuntu 12.04 for your main OS, you should use the Ubuntu 12.04 version of Virtualbox. The usual problem with Virtualbox these days is USB support - this is always a hassle. For Ubuntu 12.04 you may need to open a terminal and type

sudo usermod -a -G vboxusers yourfirstname

This should add something like 

vboxusers:x:125:yourfirstname (sorry - the face appeared unwated instead of "x")

to the last line(s) in the file named "group" in directory /etc

In Mint, this seems to add the wrong number but it seems to work fine in Ubuntu. Oddly enough, neither OS lets me just add my name as a user - it pretends to allow this but the option never works. Earlier versions did this easily. However the terminal approach, in Ubuntu 12.04 seems to work fine.

Good luck - I'll let you know if Internet connectivity works in MInt (as you used initially) and if any special Virtualbox settings were needed. Usually, it just defaults to the correct parameters, anyway I'll find out soon enough!

******************** NEW INFO **********************
I've completed the XP install on Mint Cinnamon and installed guest additions, accepting each warning as usual. The Virtualbox settings are exactly the same as I use on Ubuntu - all entries are identical except that the "Acceleration" tab under "System" in Virtualbox is ghosted (unavailable)  in Mint. The results are that shared folders show up fine in XP - so the XP to host link through Virtualbox works fine. USB support has a problem however. Also, the "network connected" icon shows up as if all's well in XP. The Network settings in XP also seem OK and the "network connected" icon lights up as if all's well. However when I open Internet Explorer it will not connect to any Internet site.

This experiment suggests that Virtualbox Internet access does not work on Mint Cinnamon as you have found, even through its network connections seem OK otherwise.

I suggest, as you propose, to change your OS to Ubuntu (12.04 seems quite stable) as Virtualbox has defined versions for each release. So far, I haven't seen any support for Mint, specifically in Virtualbox.

Despite this, I think I'll stay with Mint Cinnamon on my second notebook as I only use Virtualbox to run Mathcad (a hobby :) ) or MagicDVD copier using XP. It can run these on my other notebook(s). In any case, it has been an interesting experiment iyasin

---

### Post by iyasin on 2012-09-13
thanks a lot and and your answer it is very useful.
i am testing it.
thank again afz12.

---

### Post by iyasin on 2012-09-13
@sfz12

Wooow.....i solve my problem
thanks a a lot....your guess about wich version was true.
uninstall incorrect and install correct version and my problem is solve
connected to internet :lolflag:

---

### Post by afz12 on 2012-09-13
Great news iyasin. Thanks for posting a very interesting problem!

---

### Post by Old-Barbarossa on 2013-01-04
Folks,
Had a similar issue with Vista and XP in Virtualbox.
Upgraded to VB 4.2.6 and the Vista issue solved, connected automatically.
Still had no internet connection with XP even after trying all options mentioned above.
Then I downloaded the XP service packs on the host OS onto a usb drive and loaded them in XP in Virtualbox.
After rebooting SP3 there was automatic internet connection.
Therefore I assume it is an issue that SP3 resolves in XP.
Worked for me anyway.
Best of luck.

OB...

---

