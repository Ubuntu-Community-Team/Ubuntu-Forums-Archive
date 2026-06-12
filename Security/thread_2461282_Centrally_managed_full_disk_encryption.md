---
title: "Centrally managed full disk encryption"
date: 2021-04-27
forum: Security
---

### Post by nikolaidis2 on 2021-04-27
Greetings,

Can anyone recommend centrally managed full disk encryption solutions for Ubuntu? We are looking for the ability to comply with various standards such as HIPAA, to be able to provide proof of encryption for a lost/stolen device, and to be able to manage recovery keys in the event that the local administrator loses theirs for some reason. Similar functionality to Sophos SafeGuard from the Windows side. Can anyone recommend such as solution?

Thanks!

---

### Post by CelticWarrior on 2021-04-27
Welcome.

[https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019)

---

### Post by nikolaidis2 on 2021-04-28
Thank you. This article tells how to enable full disk encryption, but does not address my question of how to centrally manage it, or generate reports for compliance purposes.

---

### Post by TheFu on 2021-04-28
No clue about Sophos SafeGuard. Sorry.  I haven't any clue, but would look to **ansible** for reporting. 
Hopefully, at install time, the LUKS slots would get at least 2 slots used to decrypt the storage.  One for admins/corporate and 1 for the end-user.  There are 8 slots available in LUKS.  I have 3 in use on my laptop - one with a huge passphrase that I doubt I could actually type and 2 others for challenge-response Yubikey devices. I suspect there's a way to have LUKS use a network location through PXE booting to automatically decrypt storage. I've always considered that a failure, but in a corporate environment, perhaps it is the best answer? Automatic decryption for storage on the correct subnet?

Based on my experience dealing with Windows 10-15 yrs ago in corporate environments, Windows always needed a separate tool for reporting, whereas Unix systems just used a little script or devops tools like **ansible** to gather reports.  

Ansible gathers all sorts of facts about each system it runs on and those can be queried.  For example, if the company has standardized on LUKS for encryption and uses the normal Ubuntu installer to setup LUKS, then there will be an encrypted container which holds LVM objects for allocating storage as needed.
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
will clearly show the disk layout. Just filter that down to anything with "crypt" in the line using **grep** and there's your report.
Sorry, I can't test it since my encrypted laptop is asleep still.
Or
You could easily use ssh for reporting. 
Or
Assuming your backup server "pulls" backups from every client machine nightly, then those backups would have the encrypted storage mounted via the /etc/crypttab.  If there isn't a crypttab, then it isn't being used.

A competent Linux admin should be able to solve this in about 5 minutes across 50K systems. Now, if remote ssh connectivity hasn't been configured - that's an infrastructure management problem to be solved.
"cur" is the  "inventory" file of current systems on my LAN in the following command. Inventory files are an ansible thing and can be static or dynamic.
```
$ ansible -a "\lsblk -e 7 -o name,size,type,fstype,mountpoint" cur
**nextcloud | CHANGED | rc=0 >>**
NAME    SIZE TYPE FSTYPE MOUNTPOINT
sr0    1024M rom         
vda      20G disk        
&#9500;&#9472;vda1   19G part ext4   /
&#9500;&#9472;vda2    1K part        
&#9492;&#9472;vda5 1022M part swap   [SWAP]
**spam3 | CHANGED | rc=0 >>**
NAME    SIZE TYPE FSTYPE MOUNTPOINT
sr0    1024M rom         
vda      10G disk        
&#9500;&#9472;vda1    9G part ext4   /
&#9500;&#9472;vda2    1K part        
&#9492;&#9472;vda5 1022M part swap   [SWAP]
**zcs45 | CHANGED | rc=0 >>**
NAME                  SIZE TYPE FSTYPE      MOUNTPOINT
sr0                  1024M rom              
vda                    25G disk             
&#9500;&#9472;vda2                  1K part             
&#9500;&#9472;vda5               24.3G part LVM2_member 
&#9474; &#9500;&#9472;zcs45--vg-swap_1  980M lvm  swap        [SWAP]
&#9474; &#9492;&#9472;zcs45--vg-root   23.3G lvm  ext4        /
&#9492;&#9472;vda1                731M part ext2        /boot
....
**osmc | CHANGED | rc=0 >>**
NAME         SIZE TYPE FSTYPE MOUNTPOINT
mmcblk0     29.7G disk        
&#9500;&#9472;mmcblk0p1  243M part vfat   /boot
&#9492;&#9472;mmcblk0p2 29.5G part ext4   /

```
You get the idea.  The lines with "CHANGED" are the start of each systems report from Ansible.  It took me longer to write this post than the 30 seconds to get the ansible command correct. 1 or 50K systems, the command would be the same.  My example command also his a few r-pi systems and provided the storage report for them too.  Just use **tee** to put the output into a file.  Systems that aren't online look like 
```
[B]vpn | UNREACHABLE! => {
[/B]    "changed": false,
    "msg": "Failed to connect to the host via ssh: ssh: connect to host vpn port 22: No route to host",
    "unreachable": true
}

```
So you can filter on "UNREACHABLE" to build a follow-up list.  Ansible uses a text file to know which systems are included in a group. Using IP ranges or DNS name-globbing works too.  The common requirement is ssh access with a python interpreter on the systems to be queried.  BTW, I understand that Ansible can be used with Windows too, but I never got that working at home.

Anyways, hope this is helpful, at least for the reporting aspects.

---

### Post by scorp123 on 2021-04-29
> **nikolaidis2 said:**
>  Can anyone recommend centrally managed full disk encryption solutions for Ubuntu? We are looking for the ability to comply with various standards such as HIPAA ...

I know of various software suites that can do that (e.g. former employers and/or customers in the telecom sector made use of them) ... but they are all commercial + non-free and quite pricey $$$.

"The Fu" already mentioned **Ansible**. And there are also other similar projects such as **Puppet**. I think building your own solution around e.g. Ansible would be the best approach long-term since it offers the most benefits. Replacing your current commercial vendor Sophos with vendors such as e.g. Oracle (yikes!), IBM/Red Hat, MicroFocus/Novell or Kaspersky (... &#1089;&#1087;&#1072;&#1089;&#1080;&#1073;&#1086; &#1090;&#1086;&#1074;&#1072;&#1088;&#1080;&#1097;! ...) and their solutions just means you'd be trading one vendor lock-in with another, with possibly no viable way out once you're stuck in their eco-system and chain of dependencies (e.g. you can't have feature X without also buying service Y and paying for extra-license Z ...)

---

### Post by TheFu on 2021-04-29
```
$ ansible -a "\lsblk -e 7 -o name,size,type,fstype,mountpoint" cur |egrep 'rc=|crypt'
hadar | CHANGED | rc=0 >>
regulus | CHANGED | rc=0 >>
romulus | CHANGED | rc=0 >>
zcs45 | CHANGED | rc=0 >>
istar | CHANGED | rc=0 >>
spam3 | CHANGED | rc=0 >>
blog44 | CHANGED | rc=0 >>
xen41 | CHANGED | rc=0 >>
posc | CHANGED | rc=0 >>
&#9492;&#9472;sda3                          464.6G part  crypto_LUKS 
  &#9492;&#9472;sda3_crypt                  464.6G crypt LVM2_member 
osmc | CHANGED | rc=0 >>
nextcloud | CHANGED | rc=0 >>
```

wouldn't take much to turn that into a text/CSV/DB file with:
[FONT=Courier New]{hostname} = LUKS|NOLUKS[/FONT]
for every host.

As you can see - only 1 system here uses LUKS, posc.


Or use
```
$ ansible -m setup cur |tee /tmp/ansible-facts.txt
```
to get all the details that ansible's "setup" module knows about each system. It boggles the mind how much it knows, BTW.

Searching on "LUKS" .... 

```
        "ansible_device_links": {
            "ids": {
                "dm-0": [
                    "dm-name-sda3_crypt",
                    "dm-uuid-CRYPT-LUKS1-f67e63db81114836aff8f2dcb9bb32fc-sda3_crypt",
                    "lvm-pv-uuid-M3j3pO-VrTd-DmUc-kjwt-lA2B-52Se-a52mf8"
```
and elsewhere 
```
                "links": {
                    "ids": [
                        "dm-name-sda3_crypt",
                        "dm-uuid-CRYPT-LUKS1-f67e63db81114836aff8f2dcb9bb32fc-sda3_crypt",
                        "lvm-pv-uuid-M3j3pO-VrTd-DmUc-kjwt-lA2B-52Se-a52mf8"
                    ],
```
and elsewhere using "crypt"
```
                    "sda3": {
                        "holders": [
                            "sda3_crypt"
                        ],

```
Ansible is very handy for getting lots of information with 1 command from 1-50,000 systems.
It is also useful for pushing consistent configuration changes to specific types of systems. Say you want all your DBMS systems to have a specific setting, that's a perfect task for Ansible.

---

### Post by scorp123 on 2021-04-29
> **TheFu said:**
>  Ansible is very handy for getting lots of information with 1 command from 1-50,000 systems. 

You can also regularly collect all that information (e.g. have the "setup" module run regularly) and create pleasantly looking web-based reports with all that information:
[https://github.com/fboender/ansible-cmdb]("https://github.com/fboender/ansible-cmdb")

Example output e.g. here: [https://rawgit.com/fboender/ansible-cmdb/master/example/html_fancy.html]("https://rawgit.com/fboender/ansible-cmdb/master/example/html_fancy.html")

Managers love this stuff :mrgreen:

They find the "black & white" terminal output from Ansible "boooooring" ... but nice looking reports they can click around in? Awww yeah they sure love this. :D

---

### Post by TheFu on 2021-04-29
This is starting to feel like an ansible love-fest.  

There are times when I hate Ansible, but the only thing worse than Ansible is all the other solutions. 

I've tried 4 of them and been to training on 2 of the most popular.   20 minutes with a "Quick Start" video and Ansible was already up and working for simple stuff.  

I still use a bash script with a loop to patch systems here, so Ansible isn't always the go-to solution. That bash script has been working for about a decade, just the list of systems in the loop has changed and I've added some updates for some specific systems like getting new ad-block lists for the pihole systems and restarting the pihole processes after patching.  What ansible brings is a common language for the solution space, which makes your skills more useful outside your current employer AND it makes hiring someone who already knows something about Ansible easier.  And if your boss likes to spend money, there are paid versions of Ansible, but those are more for "cheese" than actual capabilities.  IMHO.

I suppose Ansible could be used to create the LUKS containers and fill slot-7 with the corporate unlock key, while setting slot-0 and slot-1 to values for the local admin and the end-user of the system.  If more than 1 end-user will be on the system, give them their own LUKS slot using cryptsetup.  Challenge-response Yubikeys can be used or key files on a USB flash drive or a long, complex, random passphrase ... or all 3.  

That's why LUKS has 8 slots. Flexibility. Would be nice if password managers had 8 slots to unlock those as well.

---

### Post by nikolaidis2 on 2021-05-01
In addition to Ansible, we are definitely open to commercial offerings if you can name any. I'm not finding a lot in this space. 
Thanks!

---

### Post by scorp123 on 2021-05-03
> **nikolaidis2 said:**
> In addition to Ansible, we are definitely open to commercial offerings if you can name any. 

Well, since you asked ... maybe take a look at this:

[Kaspersky Endpoint Security for Business ADVANCED]("https://www.kaspersky.com/small-to-medium-business-security/endpoint-advanced")

[LIST]
[*]it's not "just an anti-virus", it can do a lot more (e.g. asset management, hardware inventory, etc.)
[*]it can centrally handle OS encryption too, allegedly also for Linux clients (... I never tried this myself ...)
[/LIST]

Other softwares such as e.g. Oracle Enterprise Manager, MicroFocus/Novell ZENworks, and several others can handle e.g. client inventory management and software rollout and things like that but they e.g. can't centrally manage disk encryption at all or they can't do it for Linux clients. Kaspersky is the only commercial vendor I am aware of that offers all the features you asked for also for Linux client devices, for as long as you stick to their "Business Advanced" (or better) software editions.

As for privacy concerns: All of Kaspersky's datacenters outside of Russia are located in Western countries:
[https://support.kaspersky.com/Cloud/1.0/en-US/166971.htm]("https://support.kaspersky.com/Cloud/1.0/en-US/166971.htm")

Since you mentioned compliance with norms such as HIPAA this list of datacenters might be relevant too.

---

