---
title: "mounting shared NAS folders issue"
date: 2020-03-30
forum: Server Platforms
---

### Post by alain.roger on 2020-03-30
Hi,

i already mounted several NAS shared folders via /mnt/folder-name without any issue. However i'm facing an issue right now and i do not understand what is the real problem.
I have a raid6 on my NAS and i have on it 2 shared folders: static-data and changin-data.
therefore, i created the following structure:

```
/mnt/qnap-raid6-1/static-data
/mnt/qnap-raid6-1/changing-data
```

and in my /etc/fstab, i wrote:

```
//192.168.1.100/qnap-raid6-1/static-data /mnt/qnap-raid6-1/static-data	cifs vers=1.0,x-systemd.automount,x-systemd.device-timeout=60,iocharset=utf8,credentials=/home/alain/.smbcredentials,uid=1000,gid=users,file_mode=0775,dir_mode=0775 0 0
```

while this works for any shared folders, for some unknown reason i'm not able to change owner rights on /mnt/qnap-raid6-1/static-data and it stays as root:root even if i do the same as for others: sudo chown alain:users /mnt/qnap-raid6-1/static-data

So what am i doing wrong this time ?
thx

---

### Post by TheFu on 2020-03-30
Don't use CiFS.  Use NFS.  CiFS permissions and ownsership are set by the mount options.  NFS supports the full, native, Unix permissions.
Also, is 1 min really sufficient for the mounts before they are removed?  May want to change that to 5 min - 600.
[https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156](https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156) has more details.

For CiFS people lurking, setting the CiFS version to 1.0 when connecting to Win7 or later is a bad idea for security AND performance.  v2.1 is supported by Win7.  i'd bet Win10 supports v3.0.   v1.0 would only be used when connecting to really, really, really, old, versions of Samba servers, probably from 2006 and used by a printer/scanner.

BTW, if the data should not be modified by any clients, i'd use a read-only mount.  The option is on the NFS-server, in the exports file.   For example:
```
/D/ebooks/Library       nextcloud(ro,async,root_squash) 
```
That's a read-only nfs export for epub files, to a single system, nextcloud. That is for the NAS confg.

---

### Post by Morbius1 on 2020-03-30
You might consider two more possible options in your cifs mount declaration which deals with the way the cifs client and the Samba server trade unix ownership and permissions data: **[B]nounix** [/B]&[B] noperm
[/B]
I normally add nounix  when setting up a cifs mount of a Linux samba server to insure that the uid/gid/dir_mode/file_mode is enforced for that mount for this reason. I have also seen many folks using noperm. I've never seen both used at the same time.

It is rather curious though that all the other cifs mounts to this NAS work with similar cifs statements.

---

### Post by alain.roger on 2020-04-07
I used CIFS before as my client was Windows 7 and server was running under ubuntu 14. For last 4 years i run all computers unedr linux so i guess i should update fstab with NFS instead of CIFS.
I just would like to know if there is any possibility that files on NAS used (written / read) by windows users, become not accessible or visible is i move from CIFS to NFS in fstab file, while i mount shared NAS folders (linux) ? thx

For now i changed the version of CIFS to 2.1 (instead of 1.0) and i did few tests to check speed as my NAS shares folders supportss SMB/CIFS and NFS.

here are the results
size files : less than 10 Mb/file (for a total of 568 MB):
- CIFS v2.1: desktop to NAS -> 17,89s
- NFS: desktop to NAS -> 6.88s


huge files : 3 files o 1GB + 1 file of 600MB (for a total of 3.6Gb)
- CIFS v2.1: desktop to NAS -> 67,21s
- NFS: desktop to NAS -> 35,21s

So clearly i go for NFS.

However i'm struggling to set up correctly my /etc/fstab with ntf right now

---

### Post by Morbius1 on 2020-04-07
I can only speak to CIFS as I haven't used NFS in 20 years:
>  For now i changed the version of CIFS to 2.1 (instead of 1.0).
For the version of the Linux kernel you are using and amusing your NAS can handle that dialect of smb there is no need to add any reference to versions in fstab. CIFS is designed to negotiate with the server the best dialect to use from 2.1 to 3.x. From the man pages:
> The  default  since  v4.13.5  is  for the client and server to negotiate the highest possible version greater than or
equal to 2.1. In kernels prior to v4.13, the default was 1.0. For kernels between v4.13 and v4.13.5  the  default  is
3.0.
So the only time you would need to add a vers=x.x entry is if your server is limited to the 1.0 or 2.0 dialect of smb.

Can I assume from your post that nounix and / or noperm options did not work?

---

### Post by TheFu on 2020-04-07
> **alain.roger said:**
> I used CIFS before as my client was Windows 7 and server was running under ubuntu 14. For last 4 years i run all computers unedr linux so i guess i should update fstab with NFS instead of CIFS.
I just would like to know if there is any possibility that files on NAS used (written / read) by windows users, become not accessible or visible is i move from CIFS to NFS in fstab file, while i mount shared NAS folders (linux) ? thx

For now i changed the version of CIFS to 2.1 (instead of 1.0).

Is there any reason (performance etc) to move from CIFS to NFS ?
my NAS shares folders as SMB/CIFS and NFS... but till now only CIFS mountings worked so far

NFS supports native Linux file permissions.
NFS storage looks and feels like local storage to the clients.
Updates to NFS don't break access, at least not that I've seen, er ... ever.  Samba updates sometimes break existing connections because the default configuration settings change.

NFS and Samba/CIFS are unrelated. You can run 1 or both if you like.

Performance for both are good. In general, NFS self-tunes unless you want some of the big choices that impact safety vs speed. For example, sync vs async writes.  async is faster.  sync is slower.

If you struggle with Unix file/directory permissions, then perhaps Samba would be easier. OTOH, if you want to take advantage of those elegant access controls, then Samba just won't work (without lots of server and AD setup).

Samba connections are user-to-server. Each user has credentials that need to be setup, managed, entered, etc.  Or there is a guest mode when the share is of unimportant files. There is also a forced user mode where any user allowed access will have their files written using a specific Unix/Linux userid.  These both break traceability. I would never use guest nor forced user mode, but many home networks prefer it. It can make life easier.

NFS connections are server-to-server. All users gain the access provided by normal, expected, Unix permissions. No more. No less. Behavior isn't different when local or remote. That's one of the more frustrating things about Windows File Sharing for me.

MSFT is cleaning up some baggage they've had since a LAN was 2-5 PCs. This has been causing issues for some Win10 users as things that seemed to magically work, don't work anymore.  That baggage didn't exist on Unix because networking didn't automatically allow "browse" capabilities, so Unix/Linux networking was harder for home users. The standards expect the clients to know about the servers, not for the servers to broadcast, "I'm here."  Zeroconf has been included in Ubuntu Desktops for years now attempting to make it easier - that "browse network" stuff. Zeroconf is a home-network oriented solution and really helps lots of people so they usually don't need to know much about networking.  YMMV.

When someone comes to visit your network and brings there computer, they could "browse" the network to see what's available without your permission.  If you use NFS and not Samba, they probably won't know how to connect.  That can be a good thing or a bad thing.  Nobody accidentally has NFS configured on their Windows laptop.

---

### Post by alain.roger on 2020-04-08
In fact, under NFS i feel like everybody can write/read what is shared from NAS. So the shared folder on NAS, are only accessible to people being on my local network... however, i would pleased to restrict some shared folders to only few people or to me only... so to have similar thing as i used under CIFS (so with credentials). So far i did not found it.

---

### Post by TheFu on 2020-04-08
> **alain.roger said:**
> In fact, under NFS i feel like everybody can write/read what is shared from NAS. So the shared folder on NAS, are only accessible to people being on my local network... however, i would pleased to restrict some shared folders to only few people or to me only... so to have similar thing as i used under CIFS (so with credentials). So far i did not found it.

I suspect the NAS has controls to prevent anyone from having full access to the storage, but they probably don't enable that by default to avoid customer service calls.  Time to get out the manual.  Many NAS devices have incomplete NFS implementations.  Full NFS supports a few ways to control access depending on your needs.
* static IP limitations
* userid/groupid controls
* Kerberos-based server-to-server authentication
* Kerberos-based user-to-server authentication

The NFS server will only export specific shares to specific systems, based on their IP/hostname (assuming a well-managed network).  This is the method I use along with ....
Userids and groupids using normal Unix file and directory permissions.  Usernames should be managed or carefully configured across all systems so the uid/gid for NFS users are synchronized across all systems.  How this is accomplished doesn't matter.  LDAP, NIS, NIS+, or simply making the userids manually be identical all work.  Effectively, on any system, the output from the 'id' command would be the same.  It is about the numbers, not the names.  uid=1000, gid=1001 .... the numbers need to match.  In theory, there's a /etc/idmapd.conf file to handle mappings.  I've only tried to use it once and didn't get it working. Probably user error on my part.
[https://www.qnap.com/en/how-to/tutorial/article/connecting-a-qnap-nas-to-an-ldap-directory/](https://www.qnap.com/en/how-to/tutorial/article/connecting-a-qnap-nas-to-an-ldap-directory/)

Kerberos is more complex.  Low-end NAS systems probably do not support it, though any BSD or Linux server implementation should:
[https://help.ubuntu.com/community/NFSv4Howto#NFSv4_with_Kerberos](https://help.ubuntu.com/community/NFSv4Howto#NFSv4_with_Kerberos)

---

### Post by slickymaster on 2020-04-08
*Thread moved to **Server Platforms**.*

---

### Post by alain.roger on 2020-04-08
> **TheFu said:**
> I suspect the NAS has controls to prevent anyone from having full access to the storage, but they probably don't enable that by default to avoid customer service calls.  Time to get out the manual.  Many NAS devices have incomplete NFS implementations.  Full NFS supports a few ways to control access depending on your needs.
* static IP limitations
* userid/groupid controls
* Kerberos-based server-to-server authentication
* Kerberos-based user-to-server authentication


In fact for nor it is only limited to 192.168.1.* IP, so my local network.
On my router there is a FW activated.
I find this IP limitation not really effective as i know how to fake IP, specially using WIFI... I do not use any Domain name, therefore the user/group should be the same as under CIFS... but till now i did not find where it is set :D

I do not know if QNAP TS-831 can be named as LOW-END NAS :D as it is my 2nd NAS after TheCus NAS

---

