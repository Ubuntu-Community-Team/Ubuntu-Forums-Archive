---
title: "how does OSSEC really work?"
date: 2008-03-31
forum: Security Discussions
---

### Post by pytheas22 on 2008-03-31
I've been testing OSSEC for a few days.  I have the server running on a Gutsy system with two Windows XP clients connected.  So far it's done a good job of reporting what it should be (file size changes, sketchy modifications of system logs...).  But I am still trying to figure out how exactly the product works, and I can't find this information in any documentation I've read, which includes the "manual" listed on the OSSEC website at [http://www.ossec.net/main/manual/](http://www.ossec.net/main/manual/) .

I am not asking what OSSEC looks for--I understand that basically it reports file integrity changes and log entries that it thinks are suspicious, and that this is all based on various rules configurable in an xml file, et cetera.  What I want to know is *how* OSSEC is actually keeping track of file integrity changes--how does it know when to recalculate integrity sums for a file after it's been changed?

The documentation implies (but does not explicitly say) that OSSEC parses the system directories at a fixed time interval, set in ossec.conf (by default, this was six hours on the OSSEC server, 18 hours on the Windows machines).  But what is puzzling me is that I changed the scan-time interval to a low number--fifteen minutes--and can't detect any remarkable CPU usage increases on the Windows machines, which I'm thinking I should see if OSSEC is going through all the files in \windows\system32 (the default directory to watch) and recalculating checksums.  Does it somehow know to only recalculate sums for files that have been modified since the last check?  If so, how does it keep track of this (I'm thinking that it could be watching disk I/O for changes, maybe)?

Thanks in advance for any information, or pointers to any documentation that could help me figure out how exactly OSSEC works, which I need to do before I'm comfortable launching it on the network of ~100 workstations that I help manage.

---

### Post by sbenson on 2008-04-07
Pytheas, 

For tracking file changes my understanding is it's a calculated checksum.

/var/ossec/bin/ossec-syscheckd
and 
/var/ossec/bin/syscheck_update

Step 1 calculate checksum
Step 2 check new checksum versus saved checksum.
Step 3 notify and then change saved checksum for files you verify.

if you cat /var/ossec/etc/ internal_options.conf:

# Syscheck checking/usage speed. To avoid large cpu/memory
# usage, you can specify how much to sleep after generating
# the checksum of X files. The default is to sleep 2 seconds
# after reading 15 files.
syscheck.sleep=2
syscheck.sleep_after=15

But, As for the details.
I'm damned if I can find where the saved checksums are.
If you find 'em please respond and let me know.

---

### Post by pytheas22 on 2008-04-09
Thanks for the response.  I agree with your understanding of how the checksums are calculated--I just find it surprising that, even given the option to make the process sleep, I can't seem to notice any performance impact at all, not even any spikes in CPU usage.  Calculating checksums should take tie up some noticeable amount of resources at least briefly, shouldn't it?

---

### Post by pytheas22 on 2008-04-09
More information: I've realized that OSSEC creates two databases--one for the registry and the other for the filesystem--of checksums inside a directory called "syscheck."  This is stored within the ossec-agent directory in Program Files.  I was able to watch it adding entries to the database files, meaning that it was calculating checksums as I sat in front of the computer.  I was surprised to find that as it was doing this, the ossec-agent.exe process was consuming no more than 10% of CPU resources, and it seemed to be niced (is this the right word when we're talking about Windows?) down so that if I executed more demanding processes, ossec-agent.exe would cease using resources until more were freed up.  So I guess my question is answered, and the reason that OSSEC doesn't cause any system performance issues is that it's well written and does its checksum calculations with minimal interference.

I would also like to know where the equivalent database file goes on Unix systems, but I don't have access to my OSSEC server now, so that will have to wait.

---

