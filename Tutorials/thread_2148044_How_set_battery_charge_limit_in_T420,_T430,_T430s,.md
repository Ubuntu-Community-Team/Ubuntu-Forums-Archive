---
title: "How set battery charge limit in T420, T430, T430s, T430u, etc in Ubuntu 12.04"
date: 2013-05-23
forum: Tutorials
---

### Post by tpmaxwell on 2013-05-23
You want to set charge limits for laptop batteries because this may lead to longer battery life in the long run. For old models of thinkpads, see tp_smapi: [http://www.thinkwiki.org/wiki/Tp_smapi](http://www.thinkwiki.org/wiki/Tp_smapi). "[COLOR=#000000][FONT=sans-serif]f you are installing on a recent Thinkpad that has an Ivy Bridge processor (X230, T430, T530, etc.), tp_smapi will not work." Below is how I successfully set the charge limits in T430u, using package tpacpi-bat.[/FONT][/COLOR]

Briefly, (1) install acpi_call; (2) find the acpi location to modify; (3) install tpacpi-bat; (4) modify.


(1) You can get acpi_call here: [https://github.com/mkottman/acpi_call](https://github.com/mkottman/acpi_call)
Extract and "cd" to that folder (in the terminal).

sudo make
sudo make install
sudo depmod -a
sudo modprobe acpi_call


(2) install acpidump

sudo apt-get acpidump
sudo acpidump -b -t DSDT -o /tmp/dsdt.aml
     (maybe an error: Wrong checksum... I got it but it is ok)
iasl -d /tmp/dsdt.aml
cat /tmp/dsdt.dsl | grep \\\\_SB\.PCI.*HKEY -o | uniq
Remember the output, mine is "\_SB.PCI0.LPCB.EC.HKEY" (thinkpad T430u)


(3) Get tpacpi-bat here: [https://github.com/teleshoes/tpacpi-bat](https://github.com/teleshoes/tpacpi-bat)

Extract and "cd" to that folder (in the terminal).
Open the tpacpi-bat file in the folder with gedit: (sudo) gedit tpacpi-bat
Change "my $aslBases = ..." to what we got in (2). I changed all of them, default, W520, L430,... all.


(4) Now you may follow the README, for example (at the tpacpi-bat folder):

sudo ./tpacpi-bat -v -s ST 0 70
is going to change the start threshold to 70%.

sudo ./tpacpi-bat -v -s SP 0 90
changes the stop at 90%.


(5) Reboot.

You WON'T notice difference in the battery icon in unity-indicator. But the voltage settles down when it is charged to 90%, for example.

Let me know any mistakes I made.

---

### Post by april-wen on 2013-08-28
Thank you. First I see battery still in charge but after a while the percentage keeps same. Very handy instruction.
update: My laptop T420 has win8 and its charging plan was also changed after instruction done. I updated to 13.10 and edited the threshold, Started from step 1 and the checksum error didn't show as last time.

---

