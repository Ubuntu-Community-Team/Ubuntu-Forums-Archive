---
title: "Creating CentOS5.x DVD images on your Ubuntu box"
date: 2010-08-13
forum: The Cafe
---

### Post by sspencerwire on 2010-08-13
I'm a network administrator, and while I use Ubuntu exclusively as my desktop at home and at work, I use CentOS versions for server installs.  I love Ubuntu, so the reasons we use CentOS for our server versions have nothing to do with Ubuntu, and more to do with the local knowledge base and installed base of our servers.

Obviously, installing today using multiple CD's (CentOS5.5 is now up to 8 of those) is cumbersome and kludgey and we, like many of the posts I've read lately on the Internet, really don't have the ability to use Torrents.  It's an internal policy-related issue for us, but for others, it just isn't feasible for their own personal reasons.  

CentOS no-longer offers, from any of the mirrors, a straight DVD.iso download.  To get around this, I wanted to create a DVD.iso from my CD images.  There are methods for doing this from a CentOS machine, but not one that I found for Ubuntu.  

Luckily, the process is not really that difficult, if you have some knowledge of scripting and some command-line experience.  Here's the procedure that I used to create the CentOS DVD iso:

**===== Requirements =====**

  * Ubuntu with the development tools installed and alien
  * Additional packages needed, wget
  * CentOS5.x CD isos downloaded to a folder.  (our example uses /mkdvdimg/dvd_sources)
  * A copy of the mkdvdiso.sh script located  here: [http://wiki.centos.org/TipsAndTricks/CDtoDVDMedia](http://wiki.centos.org/TipsAndTricks/CDtoDVDMedia)
  * A copy of the anaconda-runtime rpm for the version you are installing available from several sources including x86_64 this site: [http://centos.mirror.netelligent.ca/centos/5.5/os/x86_64/CentOS/anaconda-runtime-11.1.2.209-1.el5.centos.x86_64.rpm](http://centos.mirror.netelligent.ca/centos/5.5/os/x86_64/CentOS/anaconda-runtime-11.1.2.209-1.el5.centos.x86_64.rpm) or i386 here: [http://centos.mirror.netelligent.ca/centos/5.5/os/i386/CentOS/anaconda-runtime-11.1.2.209-1.el5.centos.i386.rpm](http://centos.mirror.netelligent.ca/centos/5.5/os/i386/CentOS/anaconda-runtime-11.1.2.209-1.el5.centos.i386.rpm) 
  * Plenty of free disk space for images and temporary files; At least 3 times the total space used by the CD isos.
  * A comfort level with script modification using your favorite editor. (our example uses vi) 
  * A comfort level of working in a terminal window and using the command line utilities
  * As of CentOS5.5 you will also need a dual-layer DVD blank and the capability to burn such a DVD.

**===== Procedure =====**

  - Create the directory "mkdvdimg" in your /home/username path
  - Create sub-directories called "/mkdvdimg/dvd_sources" and "/mkdvdimg/dvd_iso"
  - change to the "/mkdvdimg" directory and wget the anaconda-runtime file (example: wget [http://centos.mirror.netelligent.ca/centos/5.5/os/x86_64/CentOS/anaconda-runtime-11.1.2.209-1.el5.centos.x86_64.rpm](http://centos.mirror.netelligent.ca/centos/5.5/os/x86_64/CentOS/anaconda-runtime-11.1.2.209-1.el5.centos.x86_64.rpm)) [Note: Please choose the appropriate version for whatever version of the operating system you intend to run, either i386 or x86_64.]
  - sudo to the root user using sudo -s and enter your password
  - Using alien, attempt to install the rpm.  It will probably fail, and this is just fine. (example: "alien anaconda-runtime-11.1.2.209-1.el5.centos.x86_64.rpm")
  - After the install of the rpm fails, change to the directory that it created during the attempt. (example: /mkdvdimg/anaconda-runtime-11.1.2.209)
  - if you do an ls in this directory, it should have two directories, "debian" and "usr."  Execute the command "cp -Rf usr/ ../" which will copy the usr/ directory up one level (/mkdvdimg/usr)
  - using vi, open the mkdvdimg.sh script.  Search for the following "anaconda-runtime" and change the path given ("/usr/lib/anaconda-runtime/...") to ("/home/[username]/mkdvdimg/usr/lib/anaconda-runtime/...")
  - search again for anaconda-runtime and make the same change in this path, and then save and exit the script
  - the script requires a source path and a destination path plus the name of the output file that you want.  For ease of use, I made the script executable. 
  - for ease of use, make the script executable "chmod +x mkdvdimg.sh"
  - Ok, now we are ready to create the image.  In the /mkdvdimg directory, use the following syntax, substituting the [username] for your own username: "./mkdvdimg.sh /home/[username]/mkdvdimg/dvd_sources/ /home/[username]/mkdvdimg/dvd_iso/CentOS5.5_x86_64_DVD.iso" Note: substitute the version you are creating (example: CentOS5.5_i386_DVD.iso)
  - Once the iso builds, burn it to your dual-layer DVD blank using your favorite method.

**==== Disclaimer ====**

The above worked like a charm for me.  If there are dependencies that you don't have installed, you may get error messages asking you to install different packages.  You should be able to do all of this with Synaptic or with apt-get so that you have everything you need.

**==== Thanks ====**

My thanks to the original contributors of the script which included Chris Kloiber at Red Hat with modifications for CentOS  by Phil Schaffner.

---

