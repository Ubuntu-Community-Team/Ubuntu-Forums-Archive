---
title: "Strange messages during upgrade for USN-185-1"
date: 2005-09-20
forum: Server Platforms
---

### Post by istoyanov on 2005-09-20
While performing an upgrade for USN-185-1 I've got the following messages:
```
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1014.

<snip>

Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1409.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1410.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1411.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1412.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1413.
Use of uninitialized value in hash element at /usr/share/perl5/Debconf/DbDriver/File.pm line 51, <$__ANONIO__> chunk 1414.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1428.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1429.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1430.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1431.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1432.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1433.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1434.
Use of uninitialized value in hash element at /usr/share/perl5/Debconf/DbDriver/File.pm line 51, <$__ANONIO__> chunk 1467.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1853.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1854.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1856.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1858.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1859.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1860.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1864.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1866.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1867.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1869.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1870.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1875.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1876.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1878.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 1881.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4304.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4305.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4306.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4307.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4308.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4309.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4310.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4311.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4312.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4313.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4314.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4315.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4316.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4317.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4318.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4319.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4320.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4321.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4322.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4323.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4324.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4325.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4326.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4327.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4328.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4329.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4330.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4331.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4332.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4333.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4334.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4335.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4336.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4337.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4338.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4339.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4340.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4341.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4342.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4343.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4344.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4345.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4346.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4347.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4348.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4349.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4350.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4351.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4352.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4353.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4354.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4355.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4356.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4357.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4358.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4359.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4360.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4361.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4362.

<snip>

Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4566.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4567.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4568.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4569.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4570.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4571.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4572.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4573.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4574.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4575.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4576.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4577.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4578.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4579.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4580.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4581.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 4582.
```

Should I be concerned about these?

TIA!

P.S. If somebody is interested I may provide the full log (I couldn't upload it here for size constraints on uploadable files set by the forum software).

---

### Post by istoyanov on 2005-09-26
Meanwhile, I found the answer here: [http://www.linuxforum.com/forums/index.php?showtopic=44520&view=findpost&p=205306](http://www.linuxforum.com/forums/index.php?showtopic=44520&view=findpost&p=205306)

Cheers!!!

---

