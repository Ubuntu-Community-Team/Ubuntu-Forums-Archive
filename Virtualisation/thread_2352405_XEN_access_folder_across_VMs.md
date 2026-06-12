---
title: "XEN access folder across VMs"
date: 2017-02-12
forum: Virtualisation
---

### Post by tuxic777 on 2017-02-12
I have a XEN server hosting some Windows and Linux clients and I want  them to be able to share certain files.
So I decided to create one VM  (currently running under fedora linux) which does all the mounting stuff  (which is very complex in this case).
I made it all up so that this  mounting-VM contains n folders, one for each VM to share files with.
These folders content overlaps internally (using mount -o bind).

  My question is now, how do I connect these folders to the VMs that should have access to them?
So my idea was to have some sort of filesharing server running on the mounting-VM.
This server should open n different (tcp-)ports, one for each VM.
Then it would be an easy task to provide each VM access to only the port it is meant to access (using iptables inside the firewall-VM).

This way, the security relies mainly on the physical access provided by the firewall and not on some sort of user authentication.
For me as a network-guy this would be much easier to handle.

---

### Post by TheFu on 2017-02-13
Use NFS for non-Windows clients (VMs or any on the network)
and
use CIFS for Windows.

NFS provides native file system permissions, so you can control the directories and files available using normal userid/group permissions. The only trick for NFS to work is that userids and groupids need to be carefully matched (or not) across the different systems. Usually it is best if userids match, so that users on different systems have access to their files.  A common way this is used it to have every userid's HOME come from NFS and have that same directory shared across all the Unix systems on a network. When you see /export/home/pete ... that implies to me they are using NFS.  It is extremely common to do this inside company networks.

CIFS doesn't usually follow the Unix permissions, so I use the [homes] method for sharing only the user's HOME directory for Windows. This effectively makes a 1 userid = 1 share for CIFS needs.

The Xen aspect really has nothing to do with the question. Treat each VM like a physical machine and use normal network file sharing. That was the CIFS and NFS stuff above does.

---

### Post by tuxic777 on 2017-03-02
@TheFu: Thank you very much for your reply.
Unfortunately, I already knew all this information you wrote.
Maybe I should have explained that it is really important to me that the security of the system does not rely on any (complicated) user authentication mechanism, but really **only** on the physical security.
This is important, because as far as I see it, the more complicated systems get, the more likely it is that they contain severe vulnerabilities.
The isolation between users should be as strong as possible. So **security** really has priority even **over usability**!

Because of that, I want each server instance to communicate only in its own port(-range). This way, I can easily decide which network packets are routed where.
Running n instances of each server further gives me the opportunity to run them under a user with minimalized priviledges and put each one in its own chroot-jail.
(Another thing I would not be able to do when running one server instance for all users.)

Currently, I'm working on the configuration of my chroot-jails (I'm creating a script for that.) and I decided to use FTP (pure-ftpd to be specific) as a server.
(Please comment on my decisions.)

P.S.: I mentioned XEN mainly, because I was hoping that there would be a similar solution to virtfs in KVM.

---

### Post by TheFu on 2017-03-02
There's a famous quote about hypervisor security.  I'll paraphrase, because I can't find it this morning:
> If you believe that all the engineers in the tech industry, who cannot make a secure OS, will somehow magically find a way to create a virtual machine layer without any security issues that can be trusted while running said non-secure OSes, then you are sadly mistaken.

Physical security means NOT using any networking, locking the user, their data and the machine into a room, surrounded by a Faraday cage and not allowing them to bring anything in or out. I've worked at places like that for a few years.  Definitely do not trust a routing OS running inside a VM. 1 little mistake and you've lost the entire system security. There have been methods to break out of VMs for decades.  The same applies to chroot and to containers. 
Containers are slightly more secure than chroot stuff, IMHO. The great thing about containers comes from the deployment methods of allowing each container to do only 1 thing. A container should provide 1 service, no shell, no ssh. It should do 1 thing - like run apache for 1 website, nothing else.  If someone does hack in, then all that container can do is run apache for 1 website.  Actually, the Xen team had been pushing this to DoD with their micro-server architecture.

A few days ago, I created a new container as a non-root user and launched it.  From that, I gained complete root-level access of the hostOS file system. It was highly surprising to me and I hope they've corrected that issue in newer releases. Containers have flaws, just like everything else.

User authentication is easy when it is understood. User access controls can be as complex as you wish to make them.  What I suggested was NOT complex at all and would entail basic Unix security.  With NFS, each server-to-server connection can be authenticated for each specific remote file system.  Plus, with NFS, root accounts that aren't local to the storage don't gain any extra access.

The more complex a system's setup gets, the more likely you need to automate that setup using a devops tool, IMHO.

Have you looked at Qubes?  Also, virtFS is supported by QEMU and KVM. [http://www.linux-kvm.org/page/VirtFS](http://www.linux-kvm.org/page/VirtFS) I don't see where that helps security here. It is still a networked file system with POSIX permissions. 

Let me see if I understand this.  You'd like each userid to have their access limited by a firewall to a specific range of 10K ports any where on the subnet.  That is possible using iptables.  The hard part will be running a different set of services on the other system only for that single userid without impacting any other users.  Plus, part of the port  security on Unix-like systems is that only root can run services on ports under 1024, so there will need to be a range below that for each userid to access.  Interesting idea.

If you want to separate users. Get each of them 1 system and don't allow networking and have the system inside a locked room that only that user can access. No janitors.  That usually isn't realistic.  So we use shared resources and have users locked down with file permissions.  This is different than other popular OSes where file permissions were added 20 yrs after the OS was created.  With Unix-like systems, file permissions were the first layer of security created. It has been working well since the 1970s. There aren't any surprises about Unix file permissions. They are extremely well understood by normal admins.  Local and remote storage behaves the same on Unix OSes using NFS (unlike other OSes).

I wouldn't touch plain FTP if you care about security at all. Use sftp. There are many, many, many, reasons. 1 reason is that the data port used changes with every connection. Hard to setup firewall rules for that.  Plain FTP should have died out in 1994. ssh/scp/sftp only use the port specifically configured. These are very firewall friendly.

I'm so far off topic, doubt any of this will be helpful. Sorry.

---

### Post by tuxic777 on 2017-03-16
Nope, what you wrote is actually helpful. Thanks.
Giving each user his own PC without any networking is not possible. I'd like to do that nevertheless. My job would be easy in that case... ;)

By "containers" you mean something like docker-containers? I've heard about them but as I already wrote, I'm a network guy, so this is new to me. But I'll find tutorials...

Qubes OS is not a multi-user system and therefore not helping here. But yes, I know about it.

Nope, as I don't want to deal with userids, I planned to use anonymous ftp and let the jail build the environment so that each one of them accesses different data. All instances would be running on ports above 1024.
I'll look into sftp soon to find out if using specific ports really is easier with sftp. As all of this runs on one system, I don't really need encryption, but it does not hurt.
Using ssh/sshfs would enable the user shell access, which I want to avoid.

Yeah, of course I have the choice which software I want to trust and nothing is really 100% secure. But I'm trying to make it as secure as possible nevertheless.

The main problem I have with user authentication is that there is the chance of a security issue which allows one user to break into the account of some other user.
This risk is not necessary and can be avoided by using one process per user as far as I see it. That's the reason, I came up with this idea.

---

### Post by TheFu on 2017-03-16
> **tuxic777 said:**
> Nope, what you wrote is actually helpful. Thanks.
Giving each user his own PC without any networking is not possible. I'd like to do that nevertheless. My job would be easy in that case... ;)

> **tuxic777 said:**
> By "containers" you mean something like docker-containers? I've heard about them but as I already wrote, I'm a network guy, so this is new to me. But I'll find tutorials...Docker is 1 flavor of containers. There are many others. Containers are built-into Linux for a very, very, long time ... since 2006-ish.

> **tuxic777 said:**
> Qubes OS is not a multi-user system and therefore not helping here. But yes, I know about it.All Linux systems are multi-user. You have been misinformed.  The default Qubes setup is for a single user on a single machine, but that doesn't prevent multi-user use.  Unix is extremely flexible.

> **tuxic777 said:**
> Nope, as I don't want to deal with userids, I planned to use anonymous ftp and let the jail build the environment so that each one of them accesses different data. All instances would be running on ports above 1024.
I'll look into sftp soon to find out if using specific ports really is easier with sftp. As all of this runs on one system, I don't really need encryption, but it does not hurt. You cannot get away from userids.  It is core to the Unix security model. Every process runs under a userid.  Anonymous FTP should have died in 1994-ish. Avoiding userids is like avoiding breathing. Learn them. There are many capabilities, especially with the Linux kernel firewall, that are tied to userids.

> **tuxic777 said:**
> Using ssh/sshfs would enable the user shell access, which I want to avoid. You are misinformed.  You do not need to provide complete shell access for ssh to work. You can limit exactly which commands are allowed. This is a feature of ssh. Mostly people use it to allow 1 command, like a backup script, to run as root remotely. But there are infinite uses.

> **tuxic777 said:**
> Yeah, of course I have the choice which software I want to trust and nothing is really 100% secure. But I'm trying to make it as secure as possible nevertheless. That is what everyone does, to the limits of their knowledge.

> **tuxic777 said:**
> The main problem I have with user authentication is that there is the chance of a security issue which allows one user to break into the account of some other user.  There are ways around network segments as currently used too, but if a user is on a machine, there is probably a way to escalate to some other userid, that is true.  Local escalation bugs are patched within a day on Unix systems.  Redhat put out a report for 2016 which shows this. Don't know that anyone can do anything more. Plus, if the systems are locked down, then the users won't have a way to get the necessary software onto the machines anyways.  Sure, there are usually samples of the exploit posted, but those almost always require a C compiler and expertise to use it, which also limits who will be able to do anything locally.

> **tuxic777 said:**
> This risk is not necessary and can be avoided by using one process per user as far as I see it. That's the reason, I came up with this idea.  You really should be using NFSv4 with Kerberos. That won't help the Windows clients, but all the Unix clients will be secure.

---

### Post by TheFu on 2017-03-17
[https://www.slideshare.net/PLUMgrid/ebpf-and-linux-networking](https://www.slideshare.net/PLUMgrid/ebpf-and-linux-networking) might be useful. I dunno.  
And a presentation about it from b-sides SF. [https://www.youtube.com/watch?v=44nV6Mj11uw](https://www.youtube.com/watch?v=44nV6Mj11uw)

---

### Post by tuxic777 on 2017-04-26
Thank you very much, TheFu. Without your help, this would not have been possible.
I have now a running instance of my XEN server. (After 2 months, its about time...)

It was a lot more complicated than expected, but I'll summarize the current configuration:
On the mounting-vm I'm using n different openssh-server-instances, one for each VM. The configuration looks like this:

AllowAgentForwarding no
AllowTcpForwarding no
AllowStreamLocalForwarding no
ChallengeResponseAuthentication no
PasswordAuthentication no
PermitRootLogin yes
Protocol 2
PubkeyAuthentication yes
X11Forwarding no
AuthorizedKeysFile /root/.ssh/authorized_keys
Subsystem sftp internal-sftp
ForceCommand internal-sftp

As you may guess already, the client-vms are logging-in as root.
I understand that this is far from optimal, but as I already said, user management is pain in the ass for me.
The public-keys of all users are generated locally on the clients and copied to the mounting-vm into the authorized_keys-file.
The mounting-vm needs an iptables-rule (in my case, a /16-network covers all vms):
sudo iptables -I INPUT -s <all-vms-ip>/16 -j ACCEPT
Each sshd-instance is started by a command like that:
sudo /sbin/sshd -f /root/sshd_config -E /root/.ssh/log -o ChrootDirectory=<share-path-for-client-X> -p <port-for-client-X>

The firewall needs the following rule:
sudo iptables -I FORWARD -p tcp -s <client-ip> -d <mounting-vm> --dport <port-for-client-X> -j ACCEPT
Important to note here is that it does only work if both vms are running. It costed me a lot of time to find that out.

And finally the client uses:
sshfs -p <port> root@<mounting-vm>:/ /media/share

I am currently working on automating the booting-process so that I do not need 10 minutes or so for rebooting.
Thank you again for your amazing help, TheFu.

---

