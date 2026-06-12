---
title: "PXE boot, via ubuntu 7.10"
date: 2008-02-27
forum: United Kingdom Team
---

### Post by paul86uk on 2008-02-27
heres my goal : 
to create a bootable network resource of around 200 images for a large array of laptops. (sized from 400mb to 6GB)

my problem :
first off i tried doing this via fedora, but since i have no internet connection on the network im attempting to run this resource from i couldnt add or remove any packages to create the needed tftp and dhcp servers, i have the rpm's but ubuntu wont accept them.... guessing because its debian based.

so basically, i need a list of the packages i need to install, aswell as how to install them properly, and if anyone can tell me how to create a menu with sub menu's over a tftp (so i wont a massive list of images to traul through) i would much appreciate it.

PS using ubuntu desktop 7.10, tried server 7.10 but the lack of a gui scared me. as you've probably guessed im very new to linux. but have a very technically capable mind, so i do tend to pick things up quite quickly.
once again, any help would be greatly appreciated :)

---

### Post by paul86uk on 2008-03-03
ok its been over a week and not so much as a sniff at this thread... so im guessing thats either because there isnt anyone in ths community familiar enough with the system implementation im going for... in which case can i get a refferal to a site that does???

---

### Post by davit on 2008-03-03
Not sure what you are asking for.

If you need a list of packages for the [LTSP]("https://help.ubuntu.com/community/LTSPHowTo") 
do an 

sudo apt-cache search <package_guess_name>

I'm trying the PXE boot aswell so I need dhcp tftp and nis. as well as the images for the nodes(dumb terminals) as Im setting up a HPC cluster. However, I am using Webmin sometimes to see whats going on the servers, and this may help with GUI setup of your servers. 

I probably write howto  for a HPC cluster setup of diskless nodes. After, I figure out why I can not get DHCP server started.

---

### Post by paul86uk on 2008-03-04
looks like your goal is slightly diffrent from mine, yours is a network of systems with a pre-installed (ultra slim line) linux distro to stream what ever it is your wanting to stream to them on mass, my problem is the volume of machines that pass through the network is so high that pre-installing a linux distro to stream the data voids the point of streaming over the network..(ie around 120-150 laptops and 60-120 pc's)

what i want is to be able to plug a laptop into the network, hit f12 for a pxe boot, and load an image onto the laptop without ever having to handle a cd. at present we're using norton ghost as it usefully comes with its own bootable exe, but i need a link to the tftpd syslinux rpm's before i can do anything. trying to get ubuntu to download the files with an auto update command is a no no as that machine is not connected through to the internet due to security restrictions, so im having to download them to another machine and transfer them via a flash memory stick.

---

### Post by freesitebuilder on 2008-03-04
You'd probably get more responses in one of the main help forums, as they get visitors from around the world and not just the UK.

Good luck!

---

