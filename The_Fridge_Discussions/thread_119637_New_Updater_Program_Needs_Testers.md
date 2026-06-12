---
title: "New Updater Program Needs Testers"
date: 2006-01-19
forum: The Fridge Discussions
---

### Post by TheFridge on 2006-01-19

	 <p>Michael Vogt has put in a <a href="https://lists.ubuntu.com/archives/ubuntu-devel/2006-January/014700.html">call for testing</a> for the new upgrade tool for Ubuntu. The <a href="https://wiki.ubuntu.com/AutomaticUpgrade">general idea</a> is that when a new version of Ubuntu is released, that there should be an easy way to upgrade without manually editing text files. Ruben Vermeersch asked if this tool would be pushed to breezy so that existing users will be able to upgrade to Dapper when it is released; to which Michael replies:</p>
<blockquote><p>Yes, we plan to make it available in breezy-updates for a breezy->dapper upgrade.</p></blockquote>
<p>So if you&#8217;re planning on upgrading to Dapper during the development cycle, this is a good way to help test a feature that will no doubt make upgrading to the new hotness very easy. Michael has also posted <a href="http://people.ubuntu.com/~mvo/dist-upgrader/">screenshots</a>.</p>
 

	**[Link To Original Article]("http://fridge.ubuntu.com/node/231")**
	

---

### Post by alvinblank on 2006-01-20
Currently doing this after some hick-ups. Back-ports are not supported and needs to be remove from the source.list or else the upgrade won't continue.

I'm currently half-way through.

---

### Post by gravediggers on 2006-01-20
Does this cover Zubutu and Xubuntu upgrades as well?

Edit: Meant Kubuntu (not Zubuntu) - it was getting late!!

---

### Post by nocturn on 2006-01-20
[QUOTE=gravediggers]Does this cover Zubutu and Xubuntu upgrades as well?[/QUOTE]

What is Zubuntu?

---

### Post by Virogenesis on 2006-01-20
ubuntu port for the IBM zseries see [https://launchpad.net/distros/zubuntu ]("https://launchpad.net/distros/zubuntu")

This would be great for those testing ubuntu inside vmware install breezy then update

---

### Post by e99swa on 2006-01-20
Does it work for 64-bit?

---

### Post by alvinblank on 2006-01-20
Upon restarting, Xorg failed. Need to do a dkpg-reconfigure after that network failed, this I not sure how to solve. I could start it by enabling it in the network setup but it never starts proper on boot.

EDIT: Is there any command I could type to reconfig all packages? Maybe that would help.

---

### Post by gravediggers on 2006-01-20
[QUOTE=nocturn]What is Zubuntu?[/QUOTE]

I meant Kubuntu! (Original post updated)

---

### Post by veloct on 2006-01-23
[IMG]http://www.veloct.net/images/update manager error.png[/IMG]

Hope this helps. The email on the fridge link goes to the developers list and since I don't subscribe or plan to subscribe I'll just post it here.

---

### Post by jnie on 2006-01-27
[QUOTE=e99swa]Does it work for 64-bit?[/QUOTE]
I guess, this is just for 32bit Breezy?

---

### Post by schmigz on 2006-01-28
This is a great addition to Ubuntu.  Nice work.  I have never had trouble upgrading to a new release, but trying to explain it to people new to Ubuntu has been harder then one would expect.  The updater should make it easy for anyone.

---

### Post by Proleter on 2006-02-02
I got the follwing message when I tried to update do dapper.


```
Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/breezy-extras/main/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/breezy-extras/restricted/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/breezy-extras/universe/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/breezy-extras/multiverse/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/multiverse/binary-i386/Packages.gz) 404 Not Found

```

---

### Post by castrojo on 2006-02-02
You need to remove that mirrormax URL from your /etc/apt/sources.list.

---

### Post by pirast on 2006-02-02
>  Hope this helps. The email on the fridge link goes to the developers list and since I don't subscribe or plan to subscribe I'll just post it here.

Just send him the files ~/dist-upgrade.log and ~/dist-upgrade-apt.log and tell him what error message(s) you got. His email adress is michael.vogt at ubuntu.com

---

### Post by nikopol on 2006-02-06
Anyone else having trouble with the Nvidia-settings file? (upgrade fails completely) I guess that may be more of an issue for the dapper team than for this program?

---

### Post by madmetal on 2006-02-08
i tried to make an upgrade from breezey to dapper
got problems with 


E: Sub-process /usr/bin/dpkg returned an error code (1)
i do sudo dpkg --configure -a

then again sudo apt-get update

then sudo apt-get dist-upgrade finds some missing packages do
sudo apt-get dist-upgrade -f

and then..

/var/cache/apt/archives/nvidia-glx_1.0.8178+2.6.15.4-4_i386.deb
has problems to upgrade..
also cannot get these packages

[ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_p lf_dists_dapper_free_binary-i386_Packages)

[ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_p lf_dists_dapper_non-free_binary-i386_Packages)

[http://kubuntu.org](http://kubuntu.org) dapper/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde35_dists_dapper_main_binar y-i386_Packages)
(i have gnome and no kubuntu or kde so that seems(?) normal)

i see there were problems with nvidia driver and with x-org.
when i boot  after kernel unpacking i got the bios screen with red lines and nothing after that i was not able to get into ubuntu...
i finally make a new install from dapper iso.

i hope i helped a little!

---

### Post by jarondl on 2006-04-08
First, I want to congraluate you for this fabuolus invention.. It' good!

But, here is my problem.
When I started the upgrade, it said it has 2 hours left. So, I went to the living room to watch a film. When I came back it was only at the begining, with a dialog window open asking if I want to replace the existing 'login.defs' file.
So I had to click it and wait for another 2 hours... 
Does a user really have to wait in front of his computer for all the installation? couldn't the question be delayed for the end? or maybe asked at the begining?

anyway, good work you fellas

---

### Post by pirast on 2006-04-08
Please send you feedback to [email]michael.vogt@ubuntu.com[/email] , I'm not sure that he reads in the forums.. 

Thanks

---

