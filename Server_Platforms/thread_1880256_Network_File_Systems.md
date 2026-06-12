---
title: "Network File Systems"
date: 2011-11-13
forum: Server Platforms
---

### Post by pcpro215 on 2011-11-13
Hi all,

I am trying to get my client to access files on my server in a vmware setting. 

I am having difficulties trying to get the client to access the files on the server. I keep getting the message No Such File Or Directory, when I KNOW it's in there. 

This is for a class at school and I am not the only one having difficulties with it.

If anyone has any suggestions, I'd like to hear them.

Thanks for your help. :)

These are the steps I am following:

3. Create the /shared directory in root.  Put some sort of text file in there so that you have some kind of data in there.

4. In order to allow sharing of folders on our server, we need to install the NFS Server Kernel.
 
1.apt-get install nfs-kernel-server

5. Create an /export directory.  The reason we're going to do this is because we don't necessarily want remote users accessing the actual /shared directory, but rather a bound directory that points to the actual directory.  So, create a directory in root called /export.  We are next going to bind the /export directory to the real /shared directory where all the data will exist.  

6.To bind the /export directory to the /shared directory.  Accomplish this through the following command: 

1.mount --bind /shared /export

2.In order to save us from retyping that command after every reboot, we add the following line to /etc/fstab 

1./shared /export non bin 0 0

7.There are three configuration files that relate to an NFSv4 server: 

1./etc/default/nfs-kernel-server 

1.Ensure that the NEED_SVCGSSD directive equals no

2./etc/default/nfs-common 

1.Ensure the NEED_IDMAPD directive equals yes

2.Ensure the NEED_GSSD directive equals no

3./etc/exports 

1.Add the following -  /export x.x.x.x/24(rw) <<<my IP is 192.168.98.130
2.The x.x.x.x represent the address of your subnet (for example, if your server IP was 192.168.98.130, you'd enter 192.168.98.0/24)

3.This directive allows that /export directory to be accessible via remote clients

8.Restart the nfs-kernel-server service 

1./etc/init.d/nfs-kernel-server restart

9.Now moving to your client VM, install the nfs-common package 

1.apt-get install nfs-common

10.Just as we did on the server, we need to edit the /etc/default/nfs-common config file: 

1.Ensure the NEED_IDMAPD equals yes

2.Ensure the NEED_GSSD equals no

11.We need to create a folder on our client that will point to the shared /export directory.  Create a directory on root named /servershare

12.Now we have to mount the /export directory on our client 
1.mount -t nfs4 -o proto=tcp,port=2049 x.x.x.x:/export /servershare

2.The x.x.x.x represents the IP address of your server.  The /export represents the shared directory on the server.  The /servershare directory represents the local directory you created on your client.

3.To save us from retyping this after every reboot, we add the following line to /etc/fstab: 
1.x.x.x.x:/export /servershare nfs4 _netdev,auto 0 0

---

### Post by volkswagner on 2011-11-13
Take a look at [this how to]("http://ubuntuforums.org/showthread.php?t=249889").

It is dated and not specific to NFSv4.  You may need the portmap and nfs-common packages on your server.

When do you get file not found?  

You should verify you can mount on the client before adding it to your /etc/fstab.

Perhaps you should run through a basic setup before adding additional features like "mount --bind /shared /export".

---

### Post by pcpro215 on 2011-11-13
> **volkswagner said:**
> Take a look at [this how to]("http://ubuntuforums.org/showthread.php?t=249889").

It is dated and not specific to NFSv4.  You may need the portmap and nfs-common packages on your server.

When do you get file not found?  <<<I get it when I try to mount on the client.



You should verify you can mount on the client before adding it to your /etc/fstab.<<<How do I do that?

Perhaps you should run through a basic setup before adding additional features like "mount --bind /shared /export".You are probably correct about the basic setup. Like I said tho, this is for school and I'm just following what the teacher put in the learning plan. :)

---

### Post by SeijiSensei on 2011-11-13
Make sure the client has the nfs-common package installed.

---

