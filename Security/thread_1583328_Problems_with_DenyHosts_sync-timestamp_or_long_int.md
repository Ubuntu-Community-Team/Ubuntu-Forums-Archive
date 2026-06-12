---
title: "Problems with DenyHosts sync-timestamp or long int exceeds XML-RPC limits? See here."
date: 2010-09-27
forum: Security
---

### Post by MechaMechanism on 2010-09-27
If you use DenyHosts in Ubuntu Lucid 10.04, you are all but guaranteed to have the problems below.

I'm posting this solution to two problems in DenyHosts.  Solving these problems took a lot of work.  So I'm trying to make it much easier for the next person who has these problems.

The following error logs are actually one problem.  However the solution is a two step fix.

> 2010-09-27 08:59:06,673 - sync        : ERROR    [Errno 2] No such file or directory: '/var/lib/denyhosts/sync-timestamp'

2010-09-27 10:59:14,193 - sync        : ERROR    long int exceeds XML-RPC limits

Fixing the  long int exceeds XML-RPC limits.
```
sudo nano -w /usr/share/denyhosts/DenyHosts/sync.py
```
Look for the following and make the change from a to w.
>  fp = open(os.path.join(self.__work_dir,
                                   SYNC_TIMESTAMP), "a")>  fp = open(os.path.join(self.__work_dir,
                                   SYNC_TIMESTAMP), "w")

Now to fix the missing sync-timestamp file.
```
sudo touch /var/lib/denyhosts/sync-timestamp
```
But we need to also change the UNIX time in the file to something more appropriate in order to stop the error message long int exceeds XML-RPC limits.  Find the current UNIX time.
```
date +%s
```The result should look like this.```
1285624219
```Just copy and paste the UNIX time number into sync-timestamp, removing anything that may already be present in the sync-timestamp file.  Save and restart DenyHosts.

```
sudo service denyhosts restart
```

---

### Post by bodhi.zazen on 2010-09-27
Thank you for posting this information.

---

### Post by Mies on 2010-10-22
Thank you, was looking for a fix!

---

### Post by MechaMechanism on 2010-10-22
> **Mies said:**
> Thank you, was looking for a fix!
Your welcome.  :)

---

### Post by msandoy on 2011-03-30
This problem is not only for 10.04, I'm running 10.10, and had the same issue. Have to wait an hour to see if the update works this time.

Just checked, denyhosts updated successfully. 

I havent checked, is there a launchpad bug report on this issue?

---

### Post by MechaMechanism on 2011-03-30
> **msandoy said:**
> I havent checked, is there a launchpad bug report on this issue?
This issue has been fixed upstream.  I imagine Natty 11.04 has the updated package.

---

### Post by wcrigger on 2011-09-30
I'm seeing the same thing and am running Katya:

[wc 17] /var/lib/denyhosts # cat /etc/*release
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=11
DISTRIB_CODENAME=katya
DISTRIB_DESCRIPTION="Linux Mint 11 Katya"

Thanks to the OP for the fix!

---

### Post by henrikp on 2012-10-02
My thanks as well :)

---

