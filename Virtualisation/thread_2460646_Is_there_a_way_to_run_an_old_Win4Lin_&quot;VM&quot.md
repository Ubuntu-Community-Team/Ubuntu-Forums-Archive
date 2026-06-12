---
title: "Is there a way to run an old Win4Lin &quot;VM&quot;?"
date: 2021-04-15
forum: Virtualisation
---

### Post by eightsix on 2021-04-15
Twenty-ish years ago I used Win4Lin as an emulator for Win98SE. I just found the image yesterday and realized that it can be useful for something that's not directly relevant to my question. 

Rather than a harddrive image, I have a folder tree because Win4Lin used the Linux filesystem. I was hoping I might coax QEMU to run it because Win4Lin was based on QEMU, but I couldn't. Is there a way to use QEMU, VMware, or VirtualBox to run this Win4Lin installation? I looked at all three and they all seem to want .img- or .vmdk-type image files. 

Thanks!

---

### Post by slickymaster on 2021-04-15
Thread moved to **Virtualisation** for a better fit

---

### Post by CelticWarrior on 2021-04-15
Welcome.

[Win4Lin]("https://en.wikipedia.org/wiki/Win4Lin") wasn't an emulator. The Wikipedia page clearly states it was an hypervisor, although some versions seems to works as emulators but unlike a true emulator it was running a bare-bones Windows VM underneath: > **Win4Lin is a discontinued [proprietary software]("https://en.wikipedia.org/wiki/Proprietary_software") application for [Linux]("https://en.wikipedia.org/wiki/Linux") which allowed users to run a copy of [Windows 9x]("https://en.wikipedia.org/wiki/Windows_9x"), [Windows 2000]("https://en.wikipedia.org/wiki/Windows_2000") or [Windows XP]("https://en.wikipedia.org/wiki/Windows_XP") applications on their [Linux]("https://en.wikipedia.org/wiki/Linux") desktop.**

There's nothing that Win4Lin did that can't be done much better with any current free hypervisors, the main ones you actually mentioned in your post. And wanting an hypervisor to run another hypervisor's "image" is nonsensical to say the least.

And anything that used to run apparently emulated with it will run much better with Wine. Again, wanting to run Win4Lin now is nonsensical.

If you want to run a Windows virtual machine you can with any of the modern hypervisors you already know. That said, if your intention is to run ANY Windows version already out of support, i.e., anything older than Windows 8, then please do NOT allow network connection for that VM.

---

### Post by eightsix on 2021-04-15
I don't want to "run Win4Lin" for the sake of running Win4Lin.
I don't want to merely run Win98. I already own vmware for such things. 

There is old Windows software installed in that Win4Lin installation that I can't re-install in a new VM. That's why I was hoping to be able to run it.

---

### Post by CelticWarrior on 2021-04-15
You won't be able to run it. It's too old, abandoned a long time ago.

---

### Post by eightsix on 2021-04-16
I did it.

This was what I did on my Windows laptop:
1) I used VMware to create a Win98SE VM, and shut it down.
2) To my Ubuntu VM,
    * I added the Win98 harddrive image as an additional drive.
    * I also shared a folder of the Win4Lin files.
4) I booted to Ubuntu, then copied/overwrote the contents of the Win98 hard drive with the Win4Lin files.
5) Then I shutdown Ubuntu and booted Win98. Booting failed, so...
6) Changed the boot order in the Win98 BIOS, booted to CD, and then selected [B][2] Start computer
with CD-ROM support[/B].
7) Once booted, I switched to D: and ran **SETUP /pf** to fix the boot issue.
8) It then booted successfully to Windows 98 and I installed VMware tools. 

The boot sequence complains about a couple of missing files, but I haven't noticed any loss of functionality. Anyway--and most importantly--I can open mystery data files that can only be opened with software in that VM. Huzzah!

---

