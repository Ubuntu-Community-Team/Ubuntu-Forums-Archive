---
title: "Snortrules snapshot contains empty rules"
date: 2014-11-26
forum: Security
---

### Post by ajprameswari on 2014-11-26
[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"][/TD]
[/TR]
[/TABLE]

I configured to install Snort on my Ubuntu 12.04 which also  included  Barnyard2 and BASE installation. I am using the downloadable  rules on  Snort's website which requires me to sign up there to get the **oinkcode**. 
 But however, after I investigate the rules that I had extracted to **/etc/snort/rules** directory where all the rules are, all those rules are just plain empty.  Here is one of the rules look like

```
# Copyright 2001-2013 Sourcefire, Inc. All Rights Reserved.
#
# This file contains (i) proprietary rules that were created, tested and certified by
# Sourcefire, Inc. (the "VRT Certified Rules") that are distributed under the VRT
# Certified Rules License Agreement (v 2.0), and (ii) rules that were created by
# Sourcefire and other third parties (the "GPL Rules") that are distributed under the
# GNU General Public License (GPL), v2.
# 
# The VRT Certified Rules are owned by Sourcefire, Inc. The GPL Rules were created
# by Sourcefire and other third parties. The GPL Rules created by Sourcefire are
# owned by Sourcefire, Inc., and the GPL Rules not created by Sourcefire are owned by
# their respective creators. Please see http://www.snort.org/snort/snort-team/ for a
# list of third party owners and their respective copyrights.
# 
# In order to determine what rules are VRT Certified Rules or GPL Rules, please refer
# to the VRT Certified Rules License Agreement (v2.0).
#
#------------
# SCAN RULES
#------------
```

Can anyone help me to point out what is wrong with these rules?  
I downloaded the **snortrules-snapshot-2970.tar.gz** with the oinckode I got and used the **snort-2.9.7.0**.  
Here I also attached the snort configuration file (snort.conf) [https://www.dropbox.com/s/5db7v5wrhp59umt/snort.txt?dl=0](https://www.dropbox.com/s/5db7v5wrhp59umt/snort.txt?dl=0)

Thanks in advanced

---

