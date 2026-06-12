---
title: "Understanding Security Descriptor"
date: 2012-10-20
forum: Security
---

### Post by jamvaru on 2012-10-20
$SECURITY_DESCRIPTOR

so far I have determined it to be the ntfs way of assigning permissions, such as which file is shared on the network, etc.

I'd be happy to know more.  It seems this topic is sorely underappreciated.

My current question:

Using MyDefrag in windows I have noticed something new since using linux.  It looks for unmovable files and now finds a huge amount of $SECURITY_DESCRIPTOR files that are unmovable.  The operation takes 5 minutes to go through them all.  And of course they are unmovable, so it impairs the defrag operation.

How can I safely remove the $SECURITY_DESCRIPTOR files and keep them gone?

I have read somewhere that it is possible by automounting the ntfs drive when you boot linux, using the 'inherit' flag, which I can not find a reference to in ftab or mount man pages.

Thanks for the help.

Any info on $SECURITY_DESCRIPTORs would be helpful. :guitar:

---

### Post by cariboo on 2012-10-21
This didn't belong in Toots & Tips, moved to security discussions.

---

### Post by jamvaru on 2012-10-23
alright, so is there a tool for manipulating these?

---

### Post by CharlesA on 2012-10-23
Here you go:
[http://www.mydefrag.com/forum/index.php?topic=4172.0;wap2](http://www.mydefrag.com/forum/index.php?topic=4172.0;wap2)
[http://inform.pucp.edu.pe/~inf232/Ntfs/ntfs_doc_v0.5/attributes/security_descriptor.html](http://inform.pucp.edu.pe/~inf232/Ntfs/ntfs_doc_v0.5/attributes/security_descriptor.html)

Why not just use the Windows defrag utility?

---

### Post by jamvaru on 2012-10-24
because i prefer mydefrag, lol (windows utility is not customizable)

i found that page on mydefrag forums, too; i went into security for all my drives and made sure i had permission for everything, it ran through all the files and everything seems to be ok

the problem is with older versions of the linux ntfs protocol; the newer versions put the security descriptors all in one file; so if you are testing various versions of linux you might end up with a mess if you goof with your ntfs partitions

everything seems to be working just fine, now

still, i sort of expected a better answer, not "heres the technical crap for that"

id like to be able to manipulate my $security_descriptor data

how can i do that?

---

