---
title: "Im panicing!"
date: 2009-01-03
forum: Wine
---

### Post by daariil on 2009-01-03
Hello.

I updated wine today and after the update wine doesn't run at all. When i try to run a program in wine nothing happens. So i tried to run in a terminal and then i got this output:

"wine: Unhandled page fault on write access to 0x00452000 at address 0x7bc45faf (thread 0020), starting debugger...
wineserver crashed, please enable coredumps (ulimit -c unlimited) and restart."

So i tried to run ulimit -c unlimited but nothing happens.
I have tried to reinstall wine but the problem persisted.

Anyone have any ideas what to do?

Thanks in advance.
Cheers Daariil

---

### Post by sirdilznik on 2009-01-03
Is it wine-1.1.12?  I had problems with 1.1.12 myself.  Of course I didn't install wine through repos, instead I compiled it myself because I need to patch it.  It patched, compiled, and built fine, but then when I tried to run anything it would spit out an error message (Can't remember exactly what it was) and just hang,  Going back to 1.1.11 fixed the issue for me.

---

### Post by daariil on 2009-01-03
I dont really know what version it is. I cant even run wine config.
But if i want to go back to my old version, how do i do that?

---

### Post by sirdilznik on 2009-01-03
Here is an archived list of deb packages for wine.  Pick your poison, err... your ubuntu version, arch, and preferred wine version ;)

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Edit:  You probably want this (32-bit intepid 1.1.11): [http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.11~winehq0~ubuntu~8.10-0ubuntu1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.11~winehq0~ubuntu~8.10-0ubuntu1_i386.deb)

Or this (64-bit intrepid 1.1.11): [http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.11~winehq0~ubuntu~8.10-0ubuntu1_amd64.deb](http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.11~winehq0~ubuntu~8.10-0ubuntu1_amd64.deb)

---

### Post by matteojg on 2009-01-03
For a clean re-install of wine you need to delete the virtual windows installation: open a console and type "rm -rf $HOME/.wine".

(Note: This will delete the .wine folder completely...so all programs, settings, saved games, etc. in it will be gone).

(see the 2.6 of the WineFAQ [http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ))

After deleting the VWI do one of the following:

If you installed wine via synaptic then you can probably select wine in there and mark it for complete removal.

If you used apt-get then I think your best bet is to open a console and type "sudo apt-get remove --purge wine."

Then I would recommend installing the last stable build for your OS. I think that would be wine 1.0.1 if you have Ubuntu 8.10.

Good luck.

ps. If you want to know what version of wine you have currently installed:

Open a console and type "wine --version" or,

1. Open the Synaptic Package manager
2. Select 'Status'
3. Select 'Installed'
4. Type 'wine' in the Quick Search bar.

pps. Should you find that wine has disappeared from your apps. menu after the re-install, then try the following:

Places>Home Folder>Ctrl+H>.config>menus>applications.menu

Find this entry in the document:

<Menu>
		<Name>wine-wine</Name>
		<Deleted/>
	</Menu>

Remove the <Deleted> and save the document.

(see WineFAQ 6.27  [http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ))

---

