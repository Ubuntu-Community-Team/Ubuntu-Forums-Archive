---
title: "eucalyptus ssh problem"
date: 2009-06-14
forum: Virtualisation
---

### Post by neavin on 2009-06-14
hi,
i am using eucalyptus to create a private cloud. i am trying to add a node using:

#euca_conf -addnode <remote ip address>

the output that i get is:

/var/lib/eucalyptus
First, please run the following commands on '10.0.152.54':

sudo apt-get install eucalyptus-nc
sudo tee ~eucalyptus/.ssh/authorized_keys > /dev/null <<EOT
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEArtqwLoiNIq4FgDpgkjweZa x8vXyVN8xSPkDZCSyopylElch2fPIPLSw41G4FHp8Vt+UXCC6R QNksk/b/HMHVVRo5OYdC4Yc6wTcXZgsAGT2Q2Zi5yMIoUfXZeYbX55Ljxr 7SME7ipDUtAR6pTwFq0m60PbMg76RNIFEcYLaoCQuZ71rpRnsM PmZjcZZLlah/yHTFpuIQfaSuTaVSkNrmYQNjUvUfFtNzC9rQ7dv1mDuKKntKLa XWfrCTZ9AZLa3pUgAYKa4irnKEdEgaW/m+5pwlkov9Ibt9ny4j9Q9DVUK28MHbupo8AveL4hvlLD4ElFVe lmvF3QmYOZaBAC+dJw== eucalyptus@neavin-laptop
EOT

hit return to continue

Enter passphrase for key '/var/lib/eucalyptus/.ssh/authorized_keys': 
Enter passphrase for key '/var/lib/eucalyptus/.ssh/authorized_keys': 
Enter passphrase for key '/var/lib/eucalyptus/.ssh/authorized_keys': 
[EMAIL="eucalyptus@10.0.152.54"]eucalyptus@10.0.152.54[/EMAIL]'s password: 
Permission denied, please try again.
[EMAIL="eucalyptus@10.0.152.54"]eucalyptus@10.0.152.54[/EMAIL]'s password: 
Permission denied, please try again.
[EMAIL="eucalyptus@10.0.152.54"]eucalyptus@10.0.152.54[/EMAIL]'s password: 
Permission denied (publickey,password).
lost connection
ERROR: could not syncronize keys, check authorized_keys on 10.0.152.54, then run this command again.

the key is present in the remote computers .ssh/authorized_keys file.
the passkey entered is

ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEArtqwLoiNIq4FgDpgkjweZa x8vXyVN8xSPkDZCSyopylElch2fPIPLSw41G4FHp8Vt+UXCC6R QNksk/b/HMHVVRo5OYdC4Yc6wTcXZgsAGT2Q2Zi5yMIoUfXZeYbX55Ljxr 7SME7ipDUtAR6pTwFq0m60PbMg76RNIFEcYLaoCQuZ71rpRnsM PmZjcZZLlah/yHTFpuIQfaSuTaVSkNrmYQNjUvUfFtNzC9rQ7dv1mDuKKntKLa XWfrCTZ9AZLa3pUgAYKa4irnKEdEgaW/m+5pwlkov9Ibt9ny4j9Q9DVUK28MHbupo8AveL4hvlLD4ElFVe lmvF3QmYOZaBAC+dJw==



 the password entered was the root password of the remote computer. in spite of this, permission is denied.

is there any problem with the procedure that i have followed while setting up the ssh 
Do i need to set any passwords at the remote machine.

/etc/hosts at the remote machine @ 10.0.152.54 has :
127.0.0.1    localhost
127.0.1.1    bhavna-laptop
10.0.152.54     bhavna-eu

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts 


Please help!!!.

Thanks.

---

### Post by gowiejc on 2009-06-16
I was struggling with exactly the same situation, copying keys etc. I have just copied and pasted the command from my CC to the NC and hit enter. It did exactly what it says on the tin...

So first I ran it as my user, (Eucalyptus environment not set up, so it failed)
johno@eland:~$ euca_conf -addnode 192.168.0.200
Password:
su: Authentication failure

cat: /.ssh/id_rsa.pub: No such file or directory
ERROR: cannot read ssh key ~eucalyptus/.ssh/id_rsa.pub, syncronization will probably not work
[sudo] password for johno:
eucalyptus@192.168.0.200's password:
Permission denied, please try again.
eucalyptus@192.168.0.200's password:
Permission denied, please try again.
eucalyptus@192.168.0.200's password:
Permission denied (publickey,password).
lost connection
ERROR: could not syncronize keys, check authorized_keys on 192.168.0.200, then run this command again.

So I ran as su:
johno@eland:~$ sudo su
root@eland:/home/johno# sudo euca_conf -addnode 192.168.0.200
/var/lib/eucalyptus
First, please run the following commands on '192.168.0.200':

sudo apt-get install eucalyptus-nc
sudo tee ~eucalyptus/.ssh/authorized_keys > /dev/null <<EOT
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAuc7lPlVGPTuAe2DzgEpst+zskOiTdOzF65tOTkEUBvK5jG4jyluTNvCDNwBHIq40c+YjxVKaVR7AWLnbUxY6f7cS9n81+8JzAyK+qP+TV6akiINqSSLqy5HjkY+iyizesZIoFZzZL3QFEgVGdiCKxqR6KRiFrHYDFLTn3hA1rra3t3VR5eYk+ab/YW8GVKPyfdZyX972MKYfiy+ivTddW/E90b2jN01qZuuqi8KAlJe9AtyfAgoTa0YKcf9mzkKQw8R8gB6FSsnl/qff8zlNdhzOGqTYXhh8m0VtlYIfrWaJ+xEHxpcb1a5sxr9FqGkyWpVLg+3BYgFNRPBoEO0nnw== eucalyptus@eland
EOT

hit return to continue
*** (NB: At this stage I copied and pasted the command to the node, as I had already installed eucalyptus-nc - and hit enter, then straight back to the other node to "hit return to continue", and...)


cloud-cert.pem                                100% 1289     1.3KB/s   00:00
cloud-pk.pem                                  100% 1675     1.6KB/s   00:00
cluster-cert.pem                              100% 1289     1.3KB/s   00:00
cluster-pk.pem                                100% 1675     1.6KB/s   00:00
clusters.p12                                  100% 7482     7.3KB/s   00:00
euca.p12                                      100% 5035     4.9KB/s   00:00
nc-client-policy.xml                          100% 2834     2.8KB/s   00:00
node-cert.pem                                 100% 1289     1.3KB/s   00:00
node-pk.pem                                   100% 1679     1.6KB/s   00:00
users.p12                                     100% 4654     4.5KB/s   00:00
SUCCESS: added node '192.168.0.200' to '/etc/eucalyptus/eucalyptus.conf'
root@eland:/home/johno#

---

### Post by neavin on 2009-07-10
Yipee it worked!!!

Thanx a lot....and am sorry for replying so late....had almost given up hope...
thnx again..

---

### Post by winter2009 on 2009-07-22
> **neavin said:**
> Yipee it worked!!!

Thanx a lot....and am sorry for replying so late....had almost given up hope...
thnx again..


Hi I have the same problem with the other guy. Can you please tell us how you create the ssh key file? Thanks so much.

---

### Post by bbOne on 2009-08-06
Hi,

I have a similar problem. I have done the following step

sudo /usr/sbin/euca_conf -addnode xxx.xxx.xxx.xxx /etc/eucalyptus/eucalyptus.conf

/var/lib/eucalyptus
First, please run the following commands on 'xxx.xxx.xxx.xxx':

sudo apt-get install eucalyptus-nc
sudo tee ~eucalyptus/.ssh/authorized_keys > /dev/null <<EOT
ssh-rsa ... eucalyptus@xxxx
EOT

hit return to continue

cloud-cert.pem                                                                          100% 1289     1.3KB/s   00:00    
cloud-pk.pem                                                                            100% 1679     1.6KB/s   00:00    
cluster-cert.pem                                                                        100% 1298     1.3KB/s   00:00    
cluster-pk.pem                                                                          100% 1675     1.6KB/s   00:00    
clusters.p12                                                                            100%   12KB  12.1KB/s   00:00    
euca.p12                                                                                100% 5035     4.9KB/s   00:00    
nc-client-policy.xml                                                                    100% 2834     2.8KB/s   00:00    
node-cert.pem                                                                           100% 1298     1.3KB/s   00:00    
node-pk.pem                                                                             100% 1679     1.6KB/s   00:00    
users.p12                                                                               100% 4654     4.5KB/s   00:00    
SUCCESS: added node 'xxx.xxx.xxx.xxx' to '/etc/eucalyptus/eucalyptus.conf'

But the node does not appear in the Configuration at the Frontend?

What am I doing wrong....

---

### Post by smellydog521 on 2009-09-26
I have almost the same problem here and need help!
 
Here i'm also building a private cloud environment **only on one node, **on which there are front end(CC) and a node(NC). Finishing the eucalyptus installation and shuting the nc service down, i update the eucalyptus.conf by replacing the "VNET_BRIDGE" key value "xenbro" by "etho". And then problems comes out:
1. When i start the nc service by "sudo /etc/init.d/eucalyptus-nc start", it gives error info in log file as follows:
"libvirt: xen Daemon error: internal error failed ot connect to xend
libvirt: xen Daemon error: unbale to connect to 'localhost:8000': connection refused (code=38(thirty-eight))
errror: failed to connect to hypervisor"
2. In the registering stage, when i using "sudo euca_conf -addnode <node_hostname>" to register a node, which is all the same node in my environment, it failed again, and give some info like what you guys pasted above. I'm not sure what is the unique name of my computer, so i tryed a lot, such as "localhost", "mynode"
and my IP address, but with no result. 
3. When i entered the new OS which has been modefied by xen hypervisor, there is no connection to the internet, but in the ubuntu kernel it works, and i don't know why.
I'm also confused that whether one node is enough to build the entire enviroment, although there's some saything that it could. HELP! HELP! HELP!

---

