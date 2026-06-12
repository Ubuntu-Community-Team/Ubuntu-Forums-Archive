---
title: "Best way to Test Linux OS."
date: 2012-02-26
forum: The Cafe
---

### Post by donniezazen on 2012-02-26
Hello,

I keep installing different Linux OSs and was wondering what practices other guys prefer to not to mess too much with existing installations.

I want to keep Windows, one stable *buntu, developmental Ubuntu and may be another Linux OS.

I do not like Virtualbox.

Should I just Quadraple boot? The problem with that is I have to mess up with Grub.

Is Chroot the solution? How does it work? It means installing a Linux in another Linux. Do i get the Chroot-ed OS in the Grub menu and it behave separately along with other OSs.

Thanks.

---

### Post by 3Miro on 2012-02-26
Chroot mostly gives you a CLI terminal and if you do it right you can run some graphical applications, it is not a way to test another distribution. Chroot is a good way to fix something that is wrong with a current installation.

I have a HDD that I have split into many partitions and I install "experimental" distributions on it. I tell the distributions to install their Grub on their partition as opposed to the MBR, then I have the main distro with the MBR and I just have to enter the new entry (or in your case sudo update-grub).

---

### Post by snowpine on 2012-02-26
I choose one distro and stick with it; this is very difficult for me (I am a born distro-hopper) but it keeps me sane. :)

---

### Post by DeathShot on 2012-02-26
Personally I test all my OS' via a maxed out 32bit virtual machine (quad core processor 4gigs or ram) I make using VMWare Workstation on Windows 7. So far with the exception of Unity 3D everything ran out of the box for me with out me needing to do any extra work, and even Unity 3D and Gnome3 I got working with HWA.

---

### Post by sudodus on 2012-02-26
I test OS distros on separate partitions similar to what is described by *3Miro*. But I often try live sessions only, from CD USB and directly from iso files according to this link [[COLOR="Red"]_http://ubuntuforums.org/showpost.php?p=11227153&postcount=349_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11227153&postcount=349")

And I have VirtualBox for testing live sessions from iso files, installations, installed systems.

But I have to admit, that the best way would probably be to use a completely separate computer for the testing.

---

### Post by donniezazen on 2012-02-26
I wish I had no desire to try every distro out their but what can I do. I have 5 Linux devices(PC and mobile), so, just imagine how much time I need to cut Linux out for my needs.

Any ways I think I will just quadraple boot. VM does not give same experience.

BTW. Is NTFS best solution for sharing data between Windows and Linux? Does Ubuntu play nice with NTFS?

Thanks.

---

### Post by sudodus on 2012-02-26
> **donniezazen said:**
> ...
BTW. Is NTFS best solution for sharing data between Windows and Linux? Does Ubuntu play nice with NTFS?
Thanks.
Yes I think so. I use a separate ***data*** partition with NTFS for this purpose.

---

### Post by donniezazen on 2012-02-26
> **sudodus said:**
> Yes I think so. I use a separate ***data*** partition with NTFS for this purpose.

Thanks you.

---

### Post by sammiev on 2012-02-26
I love to play so I use a usb HD to backup my HD bi-weekly. Only takes me 30 min to restore it to what it was. First of all I try the new OS via live CD and if I want more I install it.

---

### Post by donniezazen on 2012-02-26
> **sammiev said:**
> I love to play so I use a usb HD to backup my HD bi-weekly. Only takes me 30 min to restore it to what it was. First of all I try the new OS via live CD and if I want more I install it.

Ubuntu is developed in fast pace which makes stable, development and windows triple boot necessary. I might try other OS like Arch and Slackware.

---

### Post by DeathShot on 2012-02-26
Aside from having the ability to switch between 5 different operating systems at the blink of an eye, VMs give me the exact same experience. Then again I never used VirtualBox I use VMWare Workstation which is commercial grade software.

As for NTFS Data partitions, it's pretty much the only thing you can do if you want windows to access it as well. It's not that bad, aside from the occasional defrag it works just as well as ext3 or 4.

As for stable, You can always use the stable version of Ubuntu or Debian, and I know plenty of people who don't dual boot windows, and some who only do it for video games. Also don't forget that you are talking about **testing** distros here, you aren't talking about using. If you don't want to burn a live CD or DVD then that is what VMs are for unless you have partitions to spare, but that just takes so much extra time.

---

