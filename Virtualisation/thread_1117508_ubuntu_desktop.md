---
title: "ubuntu desktop"
date: 2009-04-06
forum: Virtualisation
---

### Post by gishaust on 2009-04-06
i am trying to get my ubuntu 8.04 to install VMware Server Console Installation  I have used the I have followed the notes to the letter

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

It says it install perfectly but when I go to type this line into the 
terminal . 

```

gksudo vmware

```

It starts and never show the console. I need to access my vmware servers. on another machine.

Why can't it work????

---

### Post by gishaust on 2009-04-06
its official I am sick of vmware or ubuntu I don't know which one. i setup this silly vmware email server and i can't get to it. I know I should not have gone down the vm path and I should have installed ssh. It can be that hard to install a server console so I can access another computer.

---

### Post by crazyone on 2009-04-06
ok frist which version of vmware are you using. are you using server 1.0.8 or version 2. and is it being installed on your computer or another computer in the house.if i can get this information i can help. i have gottenr both server 1 and 2 to work in 8.10, and 8.04.

---

### Post by gishaust on 2009-04-06
I have got the vm server running fine they are on another computer what i need is the server console client to run on my desktop in the how to on the community forums it says that the client will run without the server that does not seem to work for me.

```

VMware Server Console Installation (Optional, Source Install Only)

By default, the VMware Server Console is installed on the same computer as VMware Server. However, it is possible to install the application on other computers and use it to access your VMware Server remotely. Installers are available for other operating systems, such as Windows. You can download the console package only from http://www.vmware.com/download/server/ and click one which version you require. Within the next page you can download the console only zip file.

To download the file:

wget http://download3.vmware.com/software/vmserver/VMware-server-linux-client-1.0.6-91891.zip

If installing the console on Ubuntu, open a Terminal and type the following commands:

cd <location>
tar zxvf VMware-server-console-<xxx>.tar.gz
cd vmware-server-console-distrib/
sudo ./vmware-install.pl

Replace <location> with the path of the directory where you saved the archive, and replace <xxx> with the version number of the package you downloaded. After having run the installer, press Alt + F2, type gksudo vmware and press Run to start the Server Console application.

If you are getting an error similar to the following when trying to run the console (probably hardy-specific):

/.../lib/vmware-server-console/bin/vmware-server-console: /.../lib/vmware-server-console/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not fou.2)

Use the following command:

cd /usr/lib/vmware-server-console/lib/ && sudo mv libgcc_s.so.1 libgcc_s.so.1.org && sudo mv libpng12.so.0 libpng12.so.0.org

If this fails, you may try copying the 'missing' file from /usr/lib/gcc/i486-linux-gnu/3.4.6/ and replacing the one distributed with the vmware server console. If you get similar error on libpng12.so.0, the file is placed in /usr/lib. You of course have to have the appropriate packages (gcc-3.4, libpng12) installed. 



```

My problem is my desktop i will not take a whole vm server and the vm server is only at text server with no gui and is not on site. So the only way I can access this is through the vmware server console client.
Because when I set it up i though I could use the console as the access point. Now I need to access the server and update. But I can because the console will not work on ubuntu.

It installs fine but when I go to start it will not give me a gui.

---

### Post by crazyone on 2009-04-06
ok, what i had to do to get the vmware server console to work right on my laptop was install all the files in the zip. what i installed also besides the console.tar.gz pacakage was the vix and the vmperlapi. after u get those installed it should work jsut fine.also run it form the comandline on ur computer with  vmware-server-console this way u can see the errors that come out. if u need anymore help post

---

