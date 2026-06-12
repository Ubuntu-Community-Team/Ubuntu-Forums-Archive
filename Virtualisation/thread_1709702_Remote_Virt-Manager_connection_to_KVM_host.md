---
title: "Remote Virt-Manager connection to KVM host"
date: 2011-03-18
forum: Virtualisation
---

### Post by iainstott on 2011-03-18
Hi guys, im trying to setup virt-manager to connect to a remote kvm host on private network.

Both systems are running ubuntu 10.10 x64 and fully updated, have set root password and ssh public keys. 

But keep getting the dreaded;-

Unable to open a connection to the libvirt management daemon

error message, the interwebz is full of reports of this, but no solutions.
I dont want to x forward virt-manager all the time, and i really dont want to switch over to fedora/rhel.

Thanks Iain

---

### Post by falko on 2011-03-19
Can you try
```
/etc/init.d/libvirt-bin restart
``` on the KVM host?

---

### Post by iainstott on 2011-03-19
Thanks for your reply.

Restarts just fine, but still can't connect through virt-manager......

---

### Post by TheR on 2011-03-20
> **iainstott said:**
> Thanks for your reply.

Restarts just fine, but still can't connect through virt-manager......

I don't know from head anymore, but does computer ask you for password when connected to remote system. If not you must install a package, which I cannot found reference now. I think it is suggested on error dialog when connection fails.

by
TheR

---

### Post by falko on 2011-03-20
If you're connecting to the KVM host for the first time, you have to type in "yes" first on the client; then a second dialogue comes up where you have to type in the actual password. Maybe you forgot to type in "yes"?

---

### Post by iainstott on 2011-03-21
Thanks for your replys guys.

Virt-manager doesnt ask for a password, just comes up with the message

> Unable to open a connection to the libvirt management daemon.

Libvirt URI is: qemu+ssh://root@192.168.1.2/system

Verify that:
 - The 'libvirtd' daemon has been started

cannot recv data: No protocol specified
Error: Can't open display: :0.0
Host key verification failed.

: Connection reset by peer

Traceback (most recent call last):
  File "/usr/local/share/virt-manager/virtManager/connection.py", line 1022, in _try_open
    None], flags)
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 111, in openAuth
    if ret is None:raise libvirtError('virConnectOpenAuth() failed')
libvirtError: cannot recv data: No protocol specified
Error: Can't open display: :0.0
Host key verification failed.

: Connection reset by peer



Have set ssh public key, root password, installed ssh-askpass which it has been throwing up on some error messages at the bottom.
Have compiled the new virt-manager directly from the website.

I had it working straight away through opensuse 11.4 live, without any of the modifications to the setup mentioned above.

Going to install fedora 15 alpha on spare partition tonight to see if that works seeing as its rhel based and main distro for kvm related packages.

If not then might see if theres a newer libvirt package availiable than the one in ubuntu repos and compile it from source on my server.

Thanks Iain


EDIT:- Forgot to add i can open terminal issue 
> 
$virsh --connect qemu+ssh://192.168.1.2/system
VIRSH# list --all


and it be connected to the remote server, so i know there arent any connectivity issues

---

### Post by w4rren on 2011-03-21
Hi,

I've had similar problems to this after testing KVM and Virt Manager.

I'm certainly no expert on this but doing the following on the client has enabled me to get Virt Manager working (this is just from notes I have made):

Virt-manager on a clean ubuntu install (client):

1. Install virt-manager
2. Install ssh-askpass
3. Install AND log in via virt-viewer
4. Reboot
5. Run virt-manager

Virt Manager now working..

Hope this helps

Edit: this was a minimal Ubuntu install. The host was Debian Lenny

---

### Post by iainstott on 2011-03-21
> **w4rren said:**
> Hi,

I've had similar problems to this after testing KVM and Virt Manager.

I'm certainly no expert on this but doing the following on the client has enabled me to get Virt Manager working (this is just from notes I have made):

Virt-manager on a clean ubuntu install (client):

1. Install virt-manager
2. Install ssh-askpass
3. Install AND log in via virt-viewer
4. Reboot
5. Run virt-manager

Virt Manager now working..

Hope this helps

Edit: this was a minimal Ubuntu install. The host was Debian Lenny

Thank you for your reply, but still no joy.
Really am at a lose end now

---

### Post by w4rren on 2011-03-21
> **iainstott said:**
> Thank you for your reply, but still no joy.
Really am at a lose end now

Have you tried deleting all the ssh keys in your client (including root)?

I have had to do this as well in the past.

---

### Post by iainstott on 2011-03-21
> **w4rren said:**
> Have you tried deleting all the ssh keys in your client (including root)?

I have had to do this as well in the past.

~/.ssh/known_hosts ???? Or other????

Sorry am quite a noob when it comes to linux.

---

### Post by w4rren on 2011-03-21
> **iainstott said:**
> ~/.ssh/known_hosts ???? Or other????

Sorry am quite a noob when it comes to linux.

I am too, so I hope someone more knowledgeable comes along to help.

I am not on Ubuntu at the moment to check, but I think from memory that when you run virt-manager you run it with sudo (root) and so the key is then stored in the another file to the usual ~/.ssh/known_hosts.

However, I can't rememer the exact path I'm afraid - I will look later.

I do know that when I deleted these keys and started virt-manager it then prompted again for me to add the keys, and then allowed me to continue.

Edit: you could see if there's anything in: /root/.ssh/known_hosts

---

### Post by TheR on 2011-03-22
<QUOTE>
if ret is None:raise libvirtError('virConnectOpenAuth() failed')
libvirtError: cannot recv data: No protocol specified
Error: Can't open display: :0.0
Host key verification failed.
</QUOTE>

(Can't open display: :0.0) This looks like X problem.  I often get this error on some computers. Sometimes it just works after restart sometimes it never works ;-( To be frank I never really got deep into what is the purpose of DISPLAY environment variable and how it should be set. 

export DISPLAY=:0.0    mostly works.


by
TheR

---

### Post by Kokopelli on 2011-03-24
It might not be the solution you are looking for but you might try adding the kvm and libvirtd groups to a normal user and using that user to connect.  I tend to dislike solutions that involve connecting via ssh to root.

I have 3 10.10 boxes, 1 a headless server, 1 a laptop with KVM/libvirtd running, and finally a laptop with just virt-manager and dependencies.  I am able to connect to the headless server from either laptop using virt-manager. (I never tried connecting between laptops but can't see why it would be a problem)

---

### Post by galacticmex on 2012-11-25
> **w4rren said:**
> Hi,

I've had similar problems to this after testing KVM and Virt Manager.

I'm certainly no expert on this but doing the following on the client has enabled me to get Virt Manager working (this is just from notes I have made):

Virt-manager on a clean ubuntu install (client):

1. Install virt-manager
2. Install ssh-askpass
3. Install AND log in via virt-viewer
4. Reboot
5. Run virt-manager

Virt Manager now working..

Hope this helps

Edit: this was a minimal Ubuntu install. The host was Debian Lenny

this worked for me
thank you

running xubuntu 12.04 in Asus eee pc 900

---

