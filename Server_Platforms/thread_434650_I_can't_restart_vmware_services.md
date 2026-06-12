---
title: "I can't restart vmware services"
date: 2007-05-06
forum: Server Platforms
---

### Post by cacharreo on 2007-05-06
Hi Everybody:

when I try to launch a VM I get the message [B]"Unable to change virtual machine power state: The process exited with an error:
End of error message"[/B].

I think the problem is because I can't restart the VMWares server services I get the next messages on the terminal:

jaime@eliux:~$ sudo /etc/init.d/vmware restart
Stopping VMware services:
Virtual machine monitor                                          done
Bridged networking on /dev/vmnet0                     done
DHCP server on /dev/vmnet1                                  done
Host-only networking on /dev/vmnet1                  done
DHCP server on /dev/vmnet8                                  done
NAT service on /dev/vmnet8                                   done
Host-only networking on /dev/vmnet8                   done
**Virtual ethernet                                                        failed**

Some ideas about this ?

---

### Post by Corvias on 2007-05-06
I just went through the ardorous task of getting VMware going. First things first: check the permissions on the folder containing the VM's files. They should be in /var/lib/vmware/Virtual Machines. I suck at setting permissions most of the time, but I would do:

chown -R <your username> <VM Dir Name>

That will set permissions for the VM's dir, and all subdirs and files inside. Then do:

chmod -R 770 <VM Dir name>

Failing that, what version of Ubuntu Server are you using (amd64 or i386), and what vmware are you using? I am assuming you are using VMware Server, but is it the official tar.gz from thier site, or is it the one from Canonical's repository?

---

### Post by cacharreo on 2007-05-06
Thank you
 The problem is not a permissions one, because a run VMWare Server like root
The version is VMWare Server 1.0.2 and the VM was working fine yesterday. So I think that the problem should be a stupid little thing that it give me the error message

---

### Post by CRIMPS on 2007-05-08
I am having the same problem:

Virtual Ethernet                                                               Failed
Unable to stop services for VMware Server


I am sure, once i fix this problem, that I will have many other problems with VMWARE:evil: 

Maybe I just need to vent...  What the hell is wrong here?  Why would a company release a "stable" or non-beta version of a program that would have this many problems/errors with installation?  I have been trying for days to get this working and I believe I am giving up now.  

Please understand that I am a linux noob.  I have been doing nothing but reading, researching and trying different installation methods and I have been able to fix each problem only to find another.  Its endless...

Z

---

### Post by AnRkey on 2007-05-16
As root I ran vmware-config.pl  and got this output, same as everyone here I think...

[I]Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop services for VMware Server

Execution aborted.[/I]

Then as root I did this to find the virtual ethernet daemon....
*ps -A |grep vm*

This shows every process that starts with the letters vm...
* 6119 ?        00:00:00 vmnet-natd*
 and then I killed the process like this

*kill 6119*

Then I ran vmware-config.pl again as root and it completed without errors.

Let me know if this works for you or more information is needed.

AnRkey

---

### Post by veloce on 2007-05-17
> **cacharreo said:**
> Hi Everybody:

when I try to launch a VM I get the message [B]"Unable to change virtual machine power state: The process exited with an error:
End of error message"[/B].


Just a quick note to watchers of this thread - obviously the above error message is not very helpful.  You can get the full text of the error message by turning on debugging  for the virtual machine.

i had this sort of hassle when I copied a vm from one machine to another using a samba share in the middle.  It lost the permissions and had completely inappropriate ones - certain files have to be executable for a start.

---

