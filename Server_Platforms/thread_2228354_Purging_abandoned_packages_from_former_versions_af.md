---
title: "Purging abandoned packages from former versions after upgrade"
date: 2014-06-06
forum: Server Platforms
---

### Post by mdlueck on 2014-06-06
I am finding a few official Ubuntu packages on servers leftover / abandoned from distro upgrades. A couple of servers in paticular should be identical, however one started out at Ubuntu 9.04 -> 10.04 -> 12.04 while the other one started out with 9.10 and then the same subsequent upgrade steps along the way.

I was seeking to track down why the latter (9.10 beginning) server insisted on having a couple of extra packages that the former (9.04 beginning) did not demand. This lead to the discovery that python2.6 did not come from the Ubuntu 12.04 repository at all... must be left behind / abandoned from an old upgrade.

Further there are some subtle package version differences which I believe account for the package requirement discrepancy.

```

Srv1debname		Srv1version			Srv2debname		Srv2version
							libdb4.8		4.8.30-11ubuntu1
							libjpeg62		6b1-2ubuntu1.1
							python-pycurl		7.19.0-4ubuntu3
							xfonts-encodings	1:1.0.4-1ubuntu1
libdns64		1:9.7.0.dfsg.P1-1ubuntu0.9	libdns64		1:9.7.0.dfsg.P1-1ubuntu0.11
libisc60		1:9.7.0.dfsg.P1-1ubuntu0.9	libisc60		1:9.7.0.dfsg.P1-1ubuntu0.11
libisccc60		1:9.7.0.dfsg.P1-1ubuntu0.9	libisccc60		1:9.7.0.dfsg.P1-1ubuntu0.11
libisccfg60		1:9.7.0.dfsg.P1-1ubuntu0.9	libisccfg60		1:9.7.0.dfsg.P1-1ubuntu0.11
libxfont1		1:1.4.4-1			libxfont1		1:1.4.4-1ubuntu0.2
hplip			3.10.2-2ubuntu2			hplip			3.10.2-2ubuntu2.1
libavahi-core6		0.6.25-1ubuntu6			libavahi-core6		0.6.25-1ubuntu6.2
libbind9-60		1:9.7.0.dfsg.P1-1ubuntu0.9	libbind9-60		1:9.7.0.dfsg.P1-1ubuntu0.11
libc6-i686		2.11.1-0ubuntu7.11		libc6-i686		2.11.1-0ubuntu7.13
libcupsdriver1		1.5.3-0ubuntu8	libcupsdriver1				1.5.3-0ubuntu8.3
liblwres60		1:9.7.0.dfsg.P1-1ubuntu0.9	liblwres60		1:9.7.0.dfsg.P1-1ubuntu0.11
libpython2.6		2.6.5-1ubuntu6.1		libpython2.6		2.6.5-1ubuntu6.2
python2.6		2.6.5-1ubuntu6.1		python2.6		2.6.5-1ubuntu6.2
python2.6-minimal	2.6.5-1ubuntu6.1		python2.6-minimal	2.6.5-1ubuntu6.2

```

For example, the python2.6 package, within aptitude, there are a couple of version columns at the far right of the screen. The second / more right column has <none> as the value whereas other packages have a valid number filled in. Is this an indicator able to identify packages which have no source within the 12.04 repository and should be purged off these servers? If so, what is the correct syntax to search for <none> values in what ever that far right version column is? I am thinking to search for possible orphan packages with syntax similar to:

```
$ aptitude search '~o'
```

And BTW, all that command outputs is packages which I have built myself and are in no official repository, so that command is not helpful for the task.

Other various commands / switch syntax's have been tried which have not been able to detect that "python2.6 is no longer part of the Ubuntu 12.04 package list" while suggesting/offering to remove the real DHCP server package. (Already turned up that Ubuntu changed names of the DHCP server at some point so purged off the old package in that case.) Most cleanup / purge commands offer to do absolutely nothing.

So, I am interested if detecting based on <none> in the farthest right column might be a better way to detect abandoned / orphaned packages left over by upgrade processes.

I am thankful,

---

