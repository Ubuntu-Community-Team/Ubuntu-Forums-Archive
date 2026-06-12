---
title: "shmat is failing with EACCESS when I'm not root"
date: 2011-07-14
forum: Server Platforms
---

### Post by MHenrichs48 on 2011-07-14
Hello,

I'm sure this is a relatively simple permissioning issue, but I can't seem to find the appropriate settings.  

I have an application that is using a shared memory region for IPC communication.  When I run this program as root, everything works beautifully.  As any other user account, however, I'm getting "Permission Denied" or EACCESS when I try to make the call to shmat.  

I somehow managed to set up the permissions correctly for the shmget call I'm using to create the shared memory segment, but I can't seem to attach it to my process.  Here are some code snippets from those function calls:

 
int fid = shmget(IPC_PRIVATE, sh_size, SHM_HUGETLB | IPC_CREAT | O_RDWR);

uint64 * data = (uint64 *) shmat(fid, NULL, 0);

The second call is the one that's failing with a permissions issue.  Let me know what I need to do to let all (or even specific) users attach shared memory segments.

Thank You!

---

