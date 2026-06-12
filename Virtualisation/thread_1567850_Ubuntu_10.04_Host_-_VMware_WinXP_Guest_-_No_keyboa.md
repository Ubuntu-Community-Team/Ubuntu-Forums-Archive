---
title: "Ubuntu 10.04 Host - VMware WinXP Guest - No keyboard/mouse input!"
date: 2010-09-04
forum: Virtualisation
---

### Post by fermulator on 2010-09-04
This is a very strange thing, and I have no idea how to troubleshoot this.  Hoping someone has either the troubleshooting experience, or even better, has experienced this problem before.

**_Here's my setup:_**
 * Ubuntu 10.04 Host ( 2.6.32-23-generic )
 * VMware ( VMware Server 2.0.2 build-203138 )
 * Windows XP Pro Guest in VMWare

**_History/Context:_**

My previous Ubuntu installation was 9.04 Jaunty.  This is the configuration I originally used to setup and install this VMware w/ WinXP Guest.  Everything worked fine (no problems).

After my format (a few months ago), and re-installation of the latest Ubuntu 10.04, I of course re-installed VMware (using [this method]("https://help.ubuntu.com/community/VMware/Server#Ubuntu%2010.04%20%28VMware%20Server%202.0.x%29")), and re-added my WinXP guest. (i.e. I kept the virtual machine files (*.vmx etc.))

Since then, this problem has existed.

**_The Problem - What Works, What Doesn't Work_**

 1. _*Connecting via the "local console"*_
   * I have a launcher shortcut as follows:
   > /home/fermulator/.mozilla/firefox/xxxxxxxx.default/extensions/VMwareVMRC@vmware.com/plugins/vmware-vmrc -h "fermmy:8333" -M "16"   , which launches the "console connection" to vmware which would have otherwise been available through the web interface.
   * When using this, it automatically powers on the guest OS.
   * At the WinXP login screen, I'm (most of the time), able to type my password, and login.
   * Once logged in however, my keyboard input no longer works.  (start button doesn't open start menu, can't press CTRL+R to get the run prompt, etc.)
   * At any time, moving my mouse around seems to freak out the console.  two things happen as I move the mouse cursor within the window:
     1. In the bottom left hand corner, the "status" flips between "To grab input, press Ctrl+G" and "To release input, press Ctrl+Alt".
     2. If num lock is on, the num lock LED on the keyboard flickers between on/off/on/off/on/off/etc.

 2._* Connecting via "remote desktop"*_
   * Lucky for me, since I'm using my previous guest OS, remote desktop was already configured.
   * If I connect to the guest WinXP OS via RDP, keyboard/mouse input works like a charm (as expected).  So, at least I can use my guest OS via RDP, but I need to use the remote console to connect USB devices, etc.

**_Discussion_**

Based on what works and what doesn't work, this leads me to suspect that there is something wrong with VMware itself, and it's "input" is all busted.  (I have no technical explanation yet for it's behaviour...)

Any thoughts or insight?

---

### Post by fermulator on 2010-09-04
Ravindran posted something in his blog about this issue here ([http://ravindrank.blogspot.com/2010/08/adventures-of-vmware-202-and-firefox-36.html](http://ravindrank.blogspot.com/2010/08/adventures-of-vmware-202-and-firefox-36.html)), however that trick did not work for me.

---

### Post by lbrty on 2010-09-08
My setup is below. I have been using this for the past two weeks and it works perfectly.

Ubuntu 10.04 LTS Lucid Lynx
VMWare Player
Install Windows operating system within VMWare Player (in my case Windows XP)
Plugin in your magicJack and your ready to make calls!

---

### Post by dcstar on 2010-09-08
> **fermulator said:**
> 
........
Any thoughts or insight?

Did you upgrade VMware Tools on the VM?

---

