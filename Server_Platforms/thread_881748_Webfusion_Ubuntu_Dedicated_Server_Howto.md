---
title: "Webfusion Ubuntu Dedicated Server Howto"
date: 2008-08-06
forum: Server Platforms
---

### Post by mwasoft on 2008-08-06
The motivation for writing the howto is to record the experience I had in getting a Dedicated Ubuntu Server from Webfusion into what I considered to be a fit state for use. Hopefully, this will be of use to others trying to do the same thing.

What I wanted was a Ubuntu server in a managed centre which came with a vanilla Ubuntu 8.04 server installation. I would then be able to configure it as I wish. The problem is that Webfusion don't seem to believe that that is what people want and instead provide Ubuntu in a constrained chroot environment that they can manage for you. If that's what you want then good luck. However, if you want full control, then read on.

Ordering a Ubuntu Dedicated Server from Webfusion is easy enough. I have done it many times before with their Fedora offerings and never had a problem &#8211; which is why I went back to them. However, this was the first time with a Ubuntu Server.

When you first &#8220;take delivery&#8221; of the server, the default option is to control it through their control and admin web pages. On the admin web page is an option that allows you to get the full root password for your server. The first thing I did on getting the server was to go straight here and get what I believed to be the root password.

After a couple of phone calls to support, the password finally worked and I was able to log in to the server using SSH. This is when the fun starts. I appeared to be logged in as root, but all was not as it should be. The kernel image was not in /boot or anywhere else. Nor were there any kernel modules. According to /proc/partitions, the system disk was /dev/sda &#8211; but this did not exist in /dev. There were also programs such as /usr/sbin/clamd that appeared in the process list but did not exist in the filesystem.:confused:

I installed &#8220;iptables&#8221;, with apt-get, as one of the first things I wanted to do was to set up a set of firewall rules. But this refused to run, saying that the appropriate modules were not installed. 

Another couple of phone calls to support and I finally found someone that was able to tell me the answer &#8211; there are two levels of root access to their servers! I was in a chroot environment that was masquerading as root. To get full root access, I have to _really_ ask for root access. That is by sending a question to support (via their website), and agreeing that they will only be responsible for hardware maintenance (fair enough &#8211; I demand the freedom to screw up my own system). Having done this I got the real root password.

Only it's not as easy as logging in using SSH. You have to first log into the chroot environment then enter &#8220;ssh localhost -p57&#8221;, as this is the only way to get to the real root &#8211; but I was in at last. Note that port 57 cannot be accessed remotely.

The whole point of the exercise is to configure the system to the way I want it, so having got control, the next thing to do is to throw out the chroot environment and restore Ubuntu to its familiar self. This is not too difficult. If you are confident enough to take control of your server then you should know what to do next. This is what I did:

1.I created a backdoor for myself should things go wrong, by entering &#8220;/usr/sbin/sshd -p 9999&#8221;. This created another sshd server on port 9999, which allowed me another way in should things go wrong.

2.I added the same command to /etc/rc.local (just before the &#8220;exit 0&#8221;) so that the backdoor would still be available after reboot.

3.I edited /etc/ssh/sshd_config to change the sshd port number from 57 back to 22.

4.Now logged in via the backdoor, I stopped the default sshd server using &#8220;/etc/init.d/ssh stop&#8221;. Killed (-TERM) the chroot sshd server (the one given by &#8220;ps ax|grep ssh&#8221; not on port 9999) and restarted the default sshd server (/etc/init.d/ssh start).

5.I also set up my firewall rules as a script that uses iptables 
(recommended), and added a call to this script from rc.local. I also installed my own public key certificate into /root/.ssh/authorized_keys to avoid the pain of having to key in the password each time.

6.I removed the links to /etc/init.d/chroot from /etc/rc0.d through to /etc/rc6.d in order to stop it being started at boot time.

7.I now rebooted the system with &#8220;shutdown -r now&#8221;.

With my fingers firmly crossed, the system did reboot and came up in the correct state. I was able to log in normally with ssh and to port 9999. The firewall rules had also been invoked.

The next stage is to get the software up-to-date. The server was configured with dapper 6.06. Although this is still under support, this is probably the best time to upgrade it to 8.04. If the upgrade goes wrong then at least I could crawl back to Webfusion, eat humble pie, and ask them to reset it back to the default installation image, without losing any important data.

To prepare it for upgrade, I entered:

apt-get update 
(to ensure all updates applied).

apt-get xauth gedit hicolor-icon-theme synaptic update-manager-core 
(this enables me to run synaptic package manager via X11 forwarding).

Once this was done, I exited the ssh connection and restarted it with the -X option. I now entered synaptic at the command line and, after a short delay, the server's Synaptic package manager appeared on my local Ubuntu Desktop. 

Checking the repositories, I removed the unknown apt.donhost.co.uk. I assume this is Webfusion's, and is used for their own updates.

In preparation for the upgrade, I removed everything I did not want, on the grounds that the less there is installed, the less there is to go wrong. I removed mysql (4.1 was installed and I wanted 5.0 anyway). I removed apache (2.0 installed and I wanted 2.2), Qmail (I prefer sendmail) and Courier (I prefer Dovecot). I also removed the daemontools and tcpserver as these no longer had anything to do.

After applying the changes and closing Synaptic, I entered &#8220;do-release-upgrade&#8221; at the command line prompt, and nervously watched the upgrade proceed (ignoring the warning that upgrade via SSH is not fully tested/supported).

Once the upgrade had done, its work &#8211; I opted to replaced any files that had been locally configured (/etc/my.cnf and /boot/grub/menu.lst specifically), and rebooted the system.

It booted successfully with the new up-to-date kernel. I then ran Synaptic again, removed the backdoor and installed the software I wanted.:)

The result is Hardy 8.04 server with the software configuration I wanted. It's up to me to maintain and support it, but then I was always intending to in the first place.

---

