---
title: "Can't ssh into my instance."
date: 2010-09-22
forum: Ubuntu Cloud and Juju
---

### Post by Ohm's Lawyer on 2010-09-22
Hello,
 So, I'm installing UEC 10.04 and I have gotten all the way through the process with no problem. I  can get an instance running, I can ping it, everything is golden….except  I can’t ssh in.
 

For whatever reason, the store is not available from my web  interface, so I have downloaded bundles from Ubuntu, Eucalyptus, and  created a custom bundle as well. All three are registered and when I  instantiate the instance and run euca-describe-instances, they show as  running. I can ping them and even see console output.
 

I’m running the command:
ssh -i mykey.priv [EMAIL="root@A.B.C.xxx"]root@A.B.C.xxx[/EMAIL]  (obviously substituting my network info. I’m also aware that ubuntu  bundles log in as ubuntu, eucalyptus bundles log in as root, and my  custom is whatever I set up).
 

After running the command, I get:
[EMAIL="root@A.B.C.xxx"]root@A.B.C.xxx[/EMAIL]‘s password:
 

Neither Ubuntu or Eucalyptus mention anything about a password, and  my custom image has two users (in addition to root), one with a  password, one without, and I still have the same problem. 
 I’ve also tried using VNC, and ftp with the same outcome. It keeps  asking for the password. I'm thinking there might be some sort of meta-data problem where it isn't injecting my key properly, but I can't find any documentation on it.


 Any ideas? Are there any default passwords I’m not aware of?
 Thanks in advance.

---

### Post by Rusty au Lait on 2010-09-23
> **Ohm's Lawyer said:**
> 

For whatever reason, the store is not available from my web  interface, so I have downloaded bundles from Ubuntu, Eucalyptus, and  created a custom bundle as well.

I&#8217;m running the command:
ssh -i mykey.priv [EMAIL="root@A.B.C.xxx"]root@A.B.C.xxx[/EMAIL]  (obviously substituting my network info. I&#8217;m also aware that ubuntu  bundles log in as ubuntu, eucalyptus bundles log in as root, and my  custom is whatever I set up).
 

After running the command, I get:
[EMAIL="root@A.B.C.xxx"]root@A.B.C.xxx[/EMAIL]&#8216;s password:
 

Wow, that's a lot of stuff.
I'd first like to find out why I couldn't get to the store. Did you create you credentials?
None of the instances from the store has user accounts, nor do they let you use passwords (See Ritty's thread).
If you used the IP address previously to ssh another host then your .ssh/known_hosts file will have an entry for the old host (especially if you terminate and restart the same instance). You must delete the line in the file to remove the old key.
But first, find out why you can't get to the store. That seem to me the first order of business.
One last thing. instances from the store do not use root to log in with. Your command line should be 'ssh -i mykey.priv _ubuntu_@A.B.C.xxx'

---

### Post by Ohm's Lawyer on 2010-09-26
> **Rusty au Lait said:**
> Wow, that's a lot of stuff.
I'd first like to find out why I couldn't get to the store. Did you create you credentials?
None of the instances from the store has user accounts, nor do they let you use passwords (See Ritty's thread).
If you used the IP address previously to ssh another host then your .ssh/known_hosts file will have an entry for the old host (especially if you terminate and restart the same instance). You must delete the line in the file to remove the old key.
But first, find out why you can't get to the store. That seem to me the first order of business.
One last thing. instances from the store do not use root to log in with. Your command line should be 'ssh -i mykey.priv _ubuntu_@A.B.C.xxx'

Thanks for your reply,
Yes I did create credentials (tried both graphically by logging in via web browser and using command line). The reason I can't get to the store, is apparently canonical has moved it... I get:
[B][COLOR=Red]Error 6: Couldn't Resolve Host
'imagestore.canonical.com'[/COLOR][/B]

Also, when I just try to get there on my own, it says the page doesn't exist. Seems to me like a hard coded address somewhere and canonical did a little restructuring of their site. I'm not incredibly worried about that.

I've also cleared out the old keys from my authorized_keys file but to no avail. All that means is that I have to accept my new instance before I can run it. It actually seems to me that the node isn't recognizing my key as an authorized method of logging in, which is what led me to the meta-data conclusion. 

Would there be any reason meta-data might not be working on my system?

Thanks again.

---

### Post by Rusty au Lait on 2010-09-27
> **Ohm's Lawyer said:**
> 
I've also cleared out the old keys from my authorized_keys file but to no avail. All that means is that I have to accept my new instance before I can run it. It actually seems to me that the node isn't recognizing my key as an authorized method of logging in, which is what led me to the meta-data conclusion. 

Would there be any reason meta-data might not be working on my system?

Thanks again.

Can you reach the store yet? I would not suspect the meta-data file yet unless you created the image yourself.

You created your credietals twice. Make sure there are not two separate mykey.priv files One might be in ~/ and one in ~/.euca

Sorry. I should have told you that only one line in the known_hosts needed to be deleted.

when you say you are logging into the NC do you mean the host NC (A.B.C.hostip) or the instance running on the host NC (from euca-describe-instances)?
Are you using Elasticfox, HybridFox, or the command line?
Inquiring(nosey) minds want to know.

---

### Post by Ohm's Lawyer on 2010-09-27
> **Rusty au Lait said:**
> Can you reach the store yet? I would not suspect the meta-data file yet unless you created the image yourself.

You created your credietals twice. Make sure there are not two separate mykey.priv files One might be in ~/ and one in ~/.euca

Sorry. I should have told you that only one line in the known_hosts needed to be deleted.

when you say you are logging into the NC do you mean the host NC (A.B.C.hostip) or the instance running on the host NC (from euca-describe-instances)?
Are you using Elasticfox, HybridFox, or the command line?
Inquiring(nosey) minds want to know.

So, it appears I had a fundamental networking dysfunction. Bear with me, this might get a little convoluted. So, I had my public network set up as a 192.168.A.B address and my private as a 10.14.C.D address. I noticed throughout the tutorials that both networks had the same first two triplets and different on the last two. I got to wondering if perhaps I should change that. After switching both public and private addresses to 192.168 addresses and differentiating the third triplet, I played with my subnet masking and managed to get everything to work.

Long story short, I now have the store AND I can ssh into my instances. Now I'm on to learning about instance persistence.

Thanks again for your help!

---

### Post by bmullan on 2010-11-02
You can't ssh as "root" into a new instance.   You can ssh as "ubuntu" into a new instance.

> **Ohm's Lawyer said:**
> Hello,
 So, I'm installing UEC 10.04 and I have gotten all the way through the process with no problem. I  can get an instance running, I can ping it, everything is golden….except  I can’t ssh in.
 

For whatever reason, the store is not available from my web  interface, so I have downloaded bundles from Ubuntu, Eucalyptus, and  created a custom bundle as well. All three are registered and when I  instantiate the instance and run euca-describe-instances, they show as  running. I can ping them and even see console output.
 

I’m running the command:
ssh -i mykey.priv [EMAIL="root@A.B.C.xxx"]root@A.B.C.xxx[/EMAIL]  (obviously substituting my network info. I’m also aware that ubuntu  bundles log in as ubuntu, eucalyptus bundles log in as root, and my  custom is whatever I set up).
 

After running the command, I get:
[EMAIL="root@A.B.C.xxx"]root@A.B.C.xxx[/EMAIL]‘s password:
 

Neither Ubuntu or Eucalyptus mention anything about a password, and  my custom image has two users (in addition to root), one with a  password, one without, and I still have the same problem. 
 I’ve also tried using VNC, and ftp with the same outcome. It keeps  asking for the password. I'm thinking there might be some sort of meta-data problem where it isn't injecting my key properly, but I can't find any documentation on it.


 Any ideas? Are there any default passwords I’m not aware of?
 Thanks in advance.

---

### Post by secure411dotorg on 2010-11-30
I could not ssh into my instances when they were on a 172.16.0.x LAN and found by looking at the console it was full of python errors saying it was unable to reach the Landscape hosts that it wants to call home to. The console output ends there.

I had a similar problem when Amazon had network issues a few months ago on a spot instance - the instance was unable to get rebooted past the point where it tried and failed to connect to Landscape...  In neither case did I want to use Landscape :(

I was hoping that when I recreated my 10.10 UEC servers on public IPs at another location they'd be able to contact Landscape and thus would finish booting. I've continued to have really wacky troubles getting things going and today I get that Bad request signature for the Store that has been reported.

---

### Post by ashishrevar on 2011-03-17
Hello there,

I am not able to ssh into my instance. It shows the error that permission denied. How to deal with this? I have tried ubuntu@IP and root@IP both, but nothing is fruitful at this point.

Is there solution related to it?

---

### Post by rabinnh on 2011-03-17
Did you launch the instance with a key pair?  You don't mention running ssh with a key file.

---

### Post by ashishrevar on 2011-03-17
Thanks for replying,
I am having my instances in running state, I have used mykey.priv with command as per given in guide.
Which IP address I have to use to login, the IP of that machine or the IP assigned to that instance which is somehow 172.19.*.* like this?
My all images are from UEC store.

---

### Post by rabinnh on 2011-03-18
What is the Public address, the Private address, and the address of the subnet that your client machine is on?

---

### Post by ashishrevar on 2011-03-27
Hello there, I am using --addressing private in my instances,

I ran the following command...
ssh -i ~/.euca/mykey.priv ubuntu@172.19.1.2

So it says,
ssh: connect to host 172.19.1.2 port 22: No route to host

Any idea?

---

### Post by ashishrevar on 2011-03-27
If I try to ping my instances,
ping 172.19.1.2

icmp_seq=1 Destination host unreachable
what is the problem?

---

### Post by Rusty au Lait on 2011-03-28
I believe you are accessing the instance through the wrong IP address. euca-describe-instances shows two IP addresses. You the operator and any client or user accesses the instance through the first IP address you see. The second is used by eucalyptus itself and is not the concern of a EUC operator user, or client.

1) Ping the NC (the IP of the machine itself, not the instance) from the CLC and/or CL. If there is no response your problem is with your basic network setup and/or hardware.

2) If you are successful with part 1, ping the first IP address in euca-describe-instance from the CLC and/or the CL. If you do not get a response you have a network problem with the bridge or iptables.

---

### Post by ashishrevar on 2011-03-29
Thanks for replying,
I am using --addressing private as I am not having pool of public IP addresses. Whenever I use watch -n5 euca-describe-instances

It shows the list of instances, My instance is having the same IP addresses.

So what to do?

---

### Post by rabinnh on 2011-04-01
Just to be sure, run

sudo iptables -P FORWARD ACCEPT

on the Cloud Controller to make sure that it is forwarding packets from the instances.

---

### Post by ashishrevar on 2011-04-12
I have used this command, bu tit doesn't work anyhow. There was no reply, no output.

sudo iptables -P FORWARD ACCEPT

Is there any other possibility to perform this?

---

### Post by rabinnh on 2011-04-13
My guess is that it is a routing problem.  If you gave us the details and what your private AND public IP addresses and subnets are, I missed it.

My suggestion is that you try to ssh to the public address first, assuming that it's on the same subnet as your controller.

---

