---
title: "Running VMConsole on Hardy while connecting to remote vmware server"
date: 2008-04-03
forum: Virtualisation
---

### Post by webramp on 2008-04-03
I was wanting to connect to a remote vmserver from my workstation running Hardy using the vmware-server-console.  I hope this helps....


Install vmware-server-console
1. download "VMWare Server Linux Client package" from [http://register.vmware.com/content/download104.html](http://register.vmware.com/content/download104.html)
   To install VMware Server Console on a Linux host ##VMware Server Administration Guide
   1   In a terminal window, if you have not done so already, become root so you can carry out the installation steps: 
       su -
   2   Change to the directory to where you saved the installer file.
       If you downloaded a .zip file from the VMware Web site, unzip the client installer archive to /tmp:
       unzip VMware-server-linux-client-<xxxx>.zip -d /tmp
       where <xxxx> is a series of numbers representing the version and build numbers.
       CAUTION  To install the VMware Server Console from a tar package, make sure the directory to which you plan to untar the tar archive does not contain any files from a previous console tar installation.
   3   Change to the /tmp directory.
       cd /tmp
   4   Do one of the following:
        Use the RPM installer. Run RPM specifying the installation file. 
        rpm -Uhv VMware-server-console-<xxxx>.i386.rpm
        where <xxxx> is a series of numbers representing the version and build numbers.
         Use the tar installer. Complete the following steps:
       a    Unpack the archive. 
            tar zxf VMware-server-console-<xxxx>.tar.gz 
            where <xxxx> is a series of numbers representing the version and build numbers.
            The archive unpacks to vmware-server-console-distrib.
	b    Run the installer.
	       cd vmware-server-console-distrib
	       ./vmware-install.pl
	c    Accept the EULA and answer the questions specifying default directories for the binary files, library files, manual files, and documentation files.
	d     If the Do you accept prompt doesn&#697;t appear, press Q to continue.
	  
  5 	Run the configuration program vmware-config-console.pl.
  NOTE      If you use the RPM installer, you must run this program separately from  the command line. If you install from the tar archive, the installer offers to launch the configuration program for you. Answer Yes when you see the prompt.
  	You see the following prompt: What port do you want the remote console to use to connect to server. [902]
  6 	If you specified a different port number when you installed the server software, enter that port number here. Otherwise, keep the default of 902.
  7	cd /usr/lib/vmware-server-console/lib/libgcc_s.so.1

	mv libgcc_s.so.1 libgcc_s.so.1.org

	cd ../libpng12.so.0

	mv libpng12.so.0 libpng12.so.0.org

  8	run gksudo vmware-server-console


The following URL is where I found out how to mv the library files in order for the console to work.
[http://whocares.de/2008/02/25/running-vmware-server-console-on-ubuntu-hardy/](http://whocares.de/2008/02/25/running-vmware-server-console-on-ubuntu-hardy/)

---

### Post by Xianath on 2008-04-07
May I suggest you rename your thread to "[HOWTO] VMware Server Console on Hardy i386"? It is very helpful and this could help get people's attention if they are looking for a solution to this problem.

Two quick notes:

1. You can just delete this library as you have a perfectly working version installed with the libgcc1 package

2. This also works for VMware Server Console 1.0.5, just tested it a few minutes ago

Cheers,
Peter

---

### Post by webramp on 2008-04-08
Thank you for the Title change suggestion.  I think your suggestion is a more approiate Title.

---

### Post by A55h4t on 2008-04-30
Thank you for this very helpful post.  Been looking for this for 2 days.:)

---

