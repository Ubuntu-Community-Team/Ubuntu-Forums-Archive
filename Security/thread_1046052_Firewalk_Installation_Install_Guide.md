---
title: "Firewalk Installation Install Guide"
date: 2009-01-21
forum: Security
---

### Post by amvx86 on 2009-01-21
All, 

I thank many of you fine men and women with the help you've provided to myself, and others. This time around i do feel that it is time I help back. 

I have come across many people with the same problems when dealing directly with the application "FireWalk." Currently, i have a script that i have written complete with a .deb package to install and configure firewalk in a matter of seconds. 

I have confirmed the application works on Ubuntu 6 to the present operating system. If there is anyone interested please let me know. I have all the instructions, and can upload (if possible) a complete script and download to help with this installation. 

Kindest Regards, 
./amvx86

---

### Post by ajack on 2009-05-27
Can you please post the instructions... thanks... :)

---

### Post by The Tronyx on 2009-05-28
> **ajack said:**
> Can you please post the instructions... thanks... :)

Hmmm....Original post was Jan 21st.  Something tells me the OP may not be watching this thread.  You might just want to send him a PM but he also hasn't been active on the forums since that post was made.

[http://ubuntuforums.org/showthread.php?t=157524](http://ubuntuforums.org/showthread.php?t=157524) looks as though it might be relevant but I am really confused...

I found some installation instructions posted 8 days after the original post was made on a guy's blog named ajack...which is your forum ID.[http://lifewithubuntu.blogspot.com/2009/01/installing-firewalk-security-tool.html](http://lifewithubuntu.blogspot.com/2009/01/installing-firewalk-security-tool.html)

---

### Post by amvx86 on 2010-06-03
Hey sorry about the hell of a long delay... Do you want the debs, that i have and the shell to get it working?

---

### Post by dino99 on 2010-06-03
is it gpl 'ed ?

---

### Post by OpSecShellshock on 2010-06-03
Seems like an awful lot of trouble to go to just for a port scanner (the things are everywhere, including the repositories). Is there something special about this one?

---

### Post by amvx86 on 2010-06-03
Well really this isn't a port scanner. It's more or less an application to test the firewalls with a TTL value. You need to rename the firewalk.deb.zip to firewalk.deb and run the sudo dpkg --install firewalk.deb you WILL have to have libs installed such as libnet and libdnet which you can find here. (I'll try to upload the last of the files in a new post). 

When you run the application after it's installed it's going to complain about a lib file post the information (as i've done this before) and i will tell you where to go... you have to make a symbolic link from the main file to a lib file (ln -s source destination) and you'd have it working.

---

### Post by amvx86 on 2010-06-03
this is the last file that is needed. 

i can't upload but this may help you: [http://linux.softpedia.com/get/Programming/Libraries/Libnet-10275.shtml](http://linux.softpedia.com/get/Programming/Libraries/Libnet-10275.shtml)

---

### Post by amvx86 on 2010-06-03
#!/bin/sh
#IF THIS INSTALLATION SCRIPT DOES NOT WORK FOR FIREWALK
#REMOVE THE #!/BIN/SH IF YOU ARE NOT USING BASH!

echo "This installation will build the core installation files for firewalk."
echo "Please wait while we test for the installation files\n presence on the local machine."
echo "Installing flex!"

apt-get install flex --yes

if [ -f firewalk.deb ]
then
	echo "The firewalk debian package has been found. [ OK ]"
else
	echo "The firewalk.deb file cannot be found. Quitting"
	exit
fi

if [ -f libnet.tar.gz ]
then
	echo "The libnet libraries have been found. [ OK ]"
else
	echo "The libnet libraries cannot be found. Quitting"
	exit
fi

if [ -f libpcap-0.9.8 ]
then
	echo "The libpcap libraries have been found. [ OK ]"
else
	echo "The libpcap libraries cannot be found. Quitting"
	exit
fi

if [ -f libdnet-1.11.tar.gz ]
then
	echo "The libdnet libraries have been found. [ OK ]"
else
	echo "The libdnet libraries cannot be found. Quitting"
	exit
fi

echo "Decompressing the tarballs..."
tar -zxvf libdnet-1.11.tar.gz
tar -zxvf libpcap-0.9.8.tar.gz
tar -zxvf libnet.tar.gz
cd libdnet-1.11
./configure && make && make install
cd ../libpcap-0.9.8
./configure && make && make install
cd ../libnet/
./configure && make && make install
cd ../
dpkg -i firewalk.deb



echo "The installation files have been installed\n"
echo "See Errors for creating symlink."

---

