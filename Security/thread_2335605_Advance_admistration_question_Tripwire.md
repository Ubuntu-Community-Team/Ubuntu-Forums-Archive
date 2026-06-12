---
title: "Advance admistration question Tripwire"
date: 2016-08-30
forum: Security
---

### Post by patrikmellq on 2016-08-30
Hello i come to the conclusion that i should download updates or upgrades with Ubuntu using -d command which download to /var/cache/apt/archives/ but not install it.
A member of this forum show me this option.

Then i reckon that if i can check MD5 sum and see that all the downloads are ok - then tripwires alert at /var should be ok and i can clear and update the tripwire database as it was a false postive (not a hack or intrusion)
Also thinking that if i download softwares into my home folder without intall, then i should get alert at /home with tripwire

But i don't feel this is all and i want a more clear overview and could see that tripwire as different attribute which might help.

```

#  
#  Property Masks
#
#  -  ignore the following properties
#  +  check the following properties
#
#  a  access timestamp (mutually exclusive with +CMSH)
#  b  number of blocks allocated
#  c  inode creation/modification timestamp
#  d  ID of device on which inode resides
#  g  group id of owner
#  i  inode number
#  l  growing files (logfiles for example)
#  m  modification timestamp
#  n  number of links
#  p  permission and file mode bits
#  r  ID of device pointed to by inode (valid only for device objects)
#  s  file size
#  t  file type
#  u  user id of owner
#
#  C  CRC-32 hash
#  H  HAVAL hash
#  M  MD5 hash
#  S  SHA hash
#

```

Which of this commands could i add to tripwire and help me compare and observe Changes and confirm is my doing and not some one else doing.
For example if i use "t" file type, then i should see what file made tripwire alert the change and i would be ok, but then again maybe a hacker or intrusion could name a file type change or add with any name.
But with combination with "s" file size i would be pretty ok.
And "p"  permission and file mode bits, just to confirm is was me who are behind the Changes/downloads/inställs.

Does any one have experience with this?
I don't want to run Ubuntu without tripwire and would like a way to confirm that is my updates and upgrades with Ubuntu that make the tripwire alert the Changes and not a hack or intrusion - so this is a administration questions how to maintain tripwire by day to day basis.
I am not worry about any one hack tripwire as i will have the database on read only removable media.

I just need a way for tripwire to give me a clear picture of what is my doing of Changes and not a hacker.

Cheers

---

