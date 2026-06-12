---
title: "PROFTP Quota"
date: 2009-01-14
forum: Server Platforms
---

### Post by craigp on 2009-01-14
I have everything working except the quota and i am not sure why. The database gets updated when a user accesses the FTP and it updates the database to let it know when the last time it was updated and how many times it has been accessed but it doesnt record the amount of data transfered and downloaded.  

I have a similar installation to here:  [http://www.nerdgirl.dk/proftpd/installation.php](http://www.nerdgirl.dk/proftpd/installation.php)

this is part of what i have in proftpd.conf


> # Update count every time user logs in
SQLLog PASS updatecount
SQLNamedQuery updatecount UPDATE "count=count+1, accessed=now() WHERE userid='%u'" ftpuser

# Update modified everytime user uploads or deletes a file
SQLLog  STOR,DELE modified
SQLNamedQuery modified UPDATE "modified=now() WHERE userid='%u'" ftpuser

# User quotas
# ===========
QuotaEngine on
QuotaDirectoryTally on
QuotaDisplayUnits Mb
QuotaShowQuotas on

SQLNamedQuery get-quota-limit SELECT "name, quota_type, per_session, limit_type, bytes_in_avail, bytes_out_avail, bytes_xfer_avail, files_in_avail, files_out_avail, files_xfer_avail FROM ftpquotalimits WHERE name = '%{0}' AND quota_type = '%{1}'"

SQLNamedQuery get-quota-tally SELECT "name, quota_type, bytes_in_used, bytes_out_used, bytes_xfer_used, files_in_used, files_out_used, files_xfer_used FROM ftpquotatallies WHERE name = '%{0}' AND quota_type = '%{1}'"

SQLNamedQuery update-quota-tally UPDATE "bytes_in_used = bytes_in_used + %{0}, bytes_out_used = bytes_out_used + %{1}, bytes_xfer_used = bytes_xfer_used + %{2}, files_in_used = files_in_used + %{3}, files_out_used = files_out_used + %{4},files_xfer_used = files_xfer_used + %{5} WHERE name = '%{6}' AND quota_type = '%{7}'" ftpquotatallies

SQLNamedQuery insert-quota-tally INSERT "%{0}, %{1}, %{2}, %{3}, %{4}, %{5}, %{6}, %{7}" ftpquotatallies


QuotaLimitTable sql:/get-quota-limit
QuotaTallyTable sql:/get-quota-tally/update-quota-tally/insert-quota-tally


SQLNamedQuery gettally  SELECT "ROUND((bytes_in_used/1048576),2) FROM ftpquotatallies WHERE name='%u'"
SQLNamedQuery getlimit  SELECT "ROUND((bytes_in_avail/1048576),2) FROM ftpquotalimits WHERE name='%u'"
SQLNamedQuery getfree   SELECT "ROUND(((ftpquotalimits.bytes_in_avail-ftpquotatallies.bytes_in_used)/1048576),2) FROM ftpquotalimits,ftpquotatallies WHERE f$

any help would be appreciated

---

### Post by Matts007 on 2009-01-28
I have the same issue and can't figure out why this happens.

It should be that allies is only updated when you set the per_session in the quotalimits table on false, but this doesn't seem to work here.

Have you found a solution yet ?

---

### Post by etorvinen on 2009-01-28
I am fairly new to ubuntu. and have my own issues myself.
But,

I installed quotas on the partition.
Read more here: [http://ubuntuforums.org/showthread.php?t=289571](http://ubuntuforums.org/showthread.php?t=289571)

Then I set the ftp deamon to only allow connections through a valid ssh account.

hope it helps.

---

### Post by Matts007 on 2009-01-28
> **etorvinen said:**
> I am fairly new to ubuntu. and have my own issues myself.
But,

I installed quotas on the partition.
Read more here: [http://ubuntuforums.org/showthread.php?t=289571](http://ubuntuforums.org/showthread.php?t=289571)

Then I set the ftp deamon to only allow connections through a valid ssh account.

hope it helps.

But that solution is not the idea behind the MySQL DB.

---

