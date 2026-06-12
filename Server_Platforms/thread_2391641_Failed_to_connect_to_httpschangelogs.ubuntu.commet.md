---
title: "Failed to connect to https://changelogs.ubuntu.com/meta-release-lts"
date: 2018-05-11
forum: Server Platforms
---

### Post by LHammonds on 2018-05-11
Anyone else getting this message on Ubuntu Server 18.04 LTS when you login (part of motd message)?

```
Failed to connect to https://changelogs.ubuntu.com/meta-release-lts. Check your Internet connection or proxy settings
```

It comes from this motd file:
```
/etc/update-motd.d/91-release-upgrade
```

Which calls this file:
```
/usr/lib/ubuntu-release-upgrader/release-upgrade-motd
```

Which downloads this file:
```
https://changelogs.ubuntu.com/meta-release-lts
```

The contents of this meta-release-lts is as follows:
```
Dist: dapper
Name: Dapper Drake
Version: 6.06 LTS
Date: Thu, 01 Jun 2006 9:00:00 UTC
Supported: 0
Description: This is the Dapper Drake release
Release-File: http://old-releases.ubuntu.com/ubuntu/dists/dapper/Release
ReleaseNotes: http://changelogs.ubuntu.com/EOLReleaseAnnouncement
UpgradeTool: http://old-releases.ubuntu.com/ubuntu/dists/dapper/main/dist-upgrader-all/current/dapper.tar.gz
UpgradeToolSignature: http://old-releases.ubuntu.com/ubuntu/dists/dapper/main/dist-upgrader-all/current/dapper.tar.gz.gpg

Dist: hardy 
Name: Hardy Heron
Version: 8.04.1 LTS
Date: Thu, 24 Apr 2008 12:00:00 UTC
Supported: 0
Description: This is the 8.04.1 LTS release
Release-File: http://old-releases.ubuntu.com/ubuntu/dists/hardy/Release
ReleaseNotes: http://changelogs.ubuntu.com/EOLReleaseAnnouncement
UpgradeTool: http://old-releases.ubuntu.com/ubuntu/dists/hardy-proposed/main/dist-upgrader-all/0.87.31/hardy.tar.gz
UpgradeToolSignature: http://old-releases.ubuntu.com/ubuntu/dists/hardy-proposed/main/dist-upgrader-all/0.87.31/hardy.tar.gz.gpg

Dist: lucid
Name: Lucid Lynx
Version: 10.04.4 LTS
Date: Thu, 29 Apr 2010 12:00:00 UTC
Supported: 0
Description: This is the 10.04.4 LTS release
Release-File: http://old-releases.ubuntu.com/ubuntu/dists/lucid/Release
ReleaseNotes: http://changelogs.ubuntu.com/EOLReleaseAnnouncement
UpgradeTool: http://old-releases.ubuntu.com/ubuntu/dists/lucid-proposed/main/dist-upgrader-all/current/lucid.tar.gz
UpgradeToolSignature: http://old-releases.ubuntu.com/ubuntu/dists/lucid-proposed/main/dist-upgrader-all/current/lucid.tar.gz.gpg

Dist: precise
Name: Precise Pangolin
Version: 12.04.5 LTS
Date: Thu, 26 Apr 2012 12:04:00 UTC
Supported: 1
Description: This is the 12.04.5 LTS release
Release-File: http://archive.ubuntu.com/ubuntu/dists/precise/Release
ReleaseNotes: http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/dist-upgrader-all/current/ReleaseAnnouncement
ReleaseNotesHtml: http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/dist-upgrader-all/current/ReleaseAnnouncement.html
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/dist-upgrader-all/current/precise.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/dist-upgrader-all/current/precise.tar.gz.gpg

Dist: trusty
Name: Trusty Tahr
Version: 14.04.5 LTS
Date: Thu, 17 Apr 2014 14:04:00 UTC
Supported: 1
Description: This is the 14.04.5 LTS release
Release-File: http://archive.ubuntu.com/ubuntu/dists/trusty/Release
ReleaseNotes: http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/dist-upgrader-all/current/ReleaseAnnouncement
ReleaseNotesHtml: http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/dist-upgrader-all/current/ReleaseAnnouncement.html
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/dist-upgrader-all/current/trusty.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/dist-upgrader-all/current/trusty.tar.gz.gpg

Dist: xenial
Name: Xenial Xerus
Version: 16.04.4 LTS
Date: Thu, 21 April 2016 16:04:00 UTC
Supported: 1
Description: This is the 16.04.4 LTS release
Release-File: http://archive.ubuntu.com/ubuntu/dists/xenial/Release
ReleaseNotes: http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/dist-upgrader-all/current/ReleaseAnnouncement
ReleaseNotesHtml: http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/dist-upgrader-all/current/ReleaseAnnouncement.html
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/dist-upgrader-all/current/xenial.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/dist-upgrader-all/current/xenial.tar.gz.gpg
```
The meta file lacks a "bionic" entry for 18.04 because there isn't a point release available yet.  However, the program doesn't seem to handle the situation where a point release does not exist yet...thus no entry.

Is this a bug that needs to be submitted or am I missing something here?  I don't remember seeing this error message a week ago when I was creating documentation on how to install Ubuntu.

**EDIT:** My environment info:

[LIST]
[*]Version: Ubuntu Server 18.04 LTS (used "alternate" ISO image to install) 
[*]Kernel: 4.15.0-20-generic x86_64 
[*]1 CPU, 1GB RAM, 2GB swap 
[*]Host: ESXi 6.0.0 
[*]Speedtest.net results: 695.96 Mbps down / 943.30 Mbps up 
[/LIST]
 
LHammonds

---

### Post by profm on 2018-05-15
Seeing the same thing here.

---

### Post by LHammonds on 2018-05-16
Hmm....I just checked the two 18.04 servers I have and the error message does not display.

Not sure what changed for it to start working correctly.  Both files still have a timestamp of May 18, 2017.

**EDIT:** I rebooted the server to see if the boot process had anything to do with it.  Still no recurrence of the original message.

LHammonds

---

### Post by miguelsan2 on 2018-06-22
Hi :)

I had the same error in a VM where I installed Ubuntu 18.04 server.


[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAycAAAFSCAIAAABnuzelAAAAA3NCSVQICAjb4U/gAAAAEHRFWHRTb2Z0d2FyZQBTaHV0dGVyY4LQCQAAIABJREFUeNrt3b P5cidGPDXfS37TruyHTgyvNHEhoE12okDQ1buv8F26kNHB/8FjoyLug3HB/8FC1gaQBLGEmYwyXZjNpi4ow1kHZRZuwb0Xvdz0Ddv35GsYlWx Ou9zweLRTeHXSwWi8Uvi8Xixdt3b56edtvtbrfdPj5 e3NzswEAoJ7b29tXr764VBAAABM45ajr/v5efgCAhbjqDA6ur68rhhpZqb2EJhUzMEHwNEZuG1upu4njxI9TDi3POl5DyqeztmRVoXj9SUmqsc7h186guf1PKVmNrB/JfzvzBcdr7PO6oPWo2 AArCzqmtf19XVZn1C77R6vKS9LOeuvDpfz6nsRiSo6l6ck1Vi5LM dxz2rMoTyU5BU5PDFC6q33CLrR/LfznzB8VrFPQzACct7wnh/pHf54df2 gVNc3y7oT9pthP6mSyQnSb/8a3 40vR3psXLkeGX1cnUe30h lh URPJfK/Oh8zSr/oTO68jyUDXWywWcm4y rtw klq9NSnb7ezoincPjN2N1O7 GS8kytqv0L/OeP0L5blWlqa8uvduqCAntUKu3j629PoT6lrOKmohFyDqGtpELrkljeStYPBZ w/n2vchT/RCT KG7EtkvNHAYVsFu7zYDpWB5dyI44fso gHYHFR1yY8oHj5Q Cnj3JW9DyrbozSHpDkoj5GOZ/GuC4AUVdqK9 40E4cex3f67veLCTkKs7PqHlY2lgiERKAqKtCGDT9FaXi0J FRG9jF C8IVe7nMs6bNKP18QdQrnvMJ68l7ujyOwbAOejcJbUyDtK08coE7 7twRL2N/jvsbGcOxF5Wdd0clJRmYvu6aHD Aq5aJ eCfx Ile58 brtHT6d0SjdkQ2tvdpE2b1JlO74VhgiApJT hJ6eRMh8YtIUCppTX8Tr7rrJG05eVW idx F9lrmj1AtGtYfKOZT/rPOiYj5zD318 cDzAuAEXKz369dGE8PqOE B8/Ty9eur9e5A3Xt3YLxIy3kKsFngF4FyAy HEJynAKtwqQgAAERdAACirnNlziHHQsVQ2ewRUOCq81QseDdwae9 r WLKxWTbSdVMIo5fhxTchuZhbW9sD155pAPLGbNMJJ4fEPrL 3yWVxu7eNS/XzvPb5n/mJjpHxyP78RX79RzscT2AKzRV1lBs4gRfXb1oKoMR5hDDy KROtDbkAx dvm DSMtfVK u4RGLfgqIuiMLjsfIstyvzHt K9Ta vvYZ1hd1DZkNMv4Nx8ZdWuNOOmu7kakXK77B3r6njPepdK7fmc/iaGlgq3q8ofZNcJVNzNW7M8FWOitb6LgP6XsbcugnqCdlqaXnP94h1C7nzj/JXX8T6NvLbZeyjm/1kKuznHV3wXKjroGtRsrVpbHCoaXI2m7oLrziE8Pc 9HO9Ss t5r924IL7FEY/iQl6086L2lj97flpjnLxbU3FBh40iX2FaW0P5Fk28d3RbM0i6tgBVFX9XFaJ/ZdueXve61ZZMdusqt8xucE6knjK9HF4 fKDvEEdTXep7v28zTxi0zt4xs5T6s8WxBywTqirt6zeuJ7NYdqYLS05Mb3eEz98ExGvmI5ZKj lIHylJuOdwkPOUnLql/B6P7c9iFl/TEOQefx7e37Ty9AX0iDtUZdx/dkY7dEY9 DUjfqHa81r/XItbPqOi4znqQpr7U2nrxHQpbNsE qn2F7sqh6AqIumPMGerLLQO6o81mujumh59oHFZXlf9URwyyzkOgAg0W5jJ oFd9DrtX3sIQ jN48LH9n7 /v2x2Zx69VLrx1jodQQ8ptyn0PdUJUedMw98XAVdST 09W1y7VPb6ru cBXmT0daWM jwetRBaP3eUd9mo8PYQiorb7XzY0ViY2KrG85mYTlb5Z2WmyhWo953TKqO5U8otsk7uaOVNwiQgxfkcO8ibuJ5UGagQGv80QXtSq9yy8jNNOwlM7OLtuzdPT7vtdrfbbh8fv725uVEorIU79bM91md76KvMc v0gend3t6 evWFcV2smGvGWR1rfTkbs/nAyom6AEE2wBQuFQEAgKgLAEDUBQCAqAsAQNQFACDqAgBA1AUAIOoCAEDUBQAg6gIAEHUBACDqAgAQdQEAIOoCABB1AQCIugAAEHUBAIi6AABEXVR0f38vG6eX/7WXJwCnHHXdHzm9a/ypxjST7ddIGTjV gaAqKvH9SdndY25vr5WsRQ ADRcld2m517bXgKvw18dB2HHSXUub2zu8Oth5UNUF0//5Q P/6qxciORSDqh9eMLE/MTSafsYCXmP7I8lM/QcezNf6gKtZfnbjeUZqice/PQ/jW9fmbVt/h24wc3q962zxcAJvL23Zvf/PaXv/r1L16//uru7u4i7OHhIfRDfP34Xw1f3vghsv7xP4VWS1whsu Jf9ibn3jx9srd30g5dKbTu5vpm0hJIXG76ekU1Nus/NStbxXPr8TzF4CK7u7uXr/ KqOvq91fNeq98hiJZ6U5QU9AZBNVtl5rF1LSaayzuvyPkc6UnUk6rgCWL 8J4 HZxNgh10C1hpEZ8pxSGbJqQvqzRccFgLOOug5DVRr9XgsMCKqEXKGxMhyX8/SDhPTrALBGGe8wNqKQc3szcWJrmQFh8 lN1UZuO/NfpaMLAE4/6mpfF7MeCeVeVjtjjoJApErscubxZZVjMVLIlZKNyDrx6LYdSk5TTzoD1njiboEAlq9k5oiC8TeRTrLDP6UsT lgC6WT FeJ2 0c1dQ5KUBxfkY98KFRWZ3LO2dAiO/XePmPbDc0KUPWzBGR495bDukdwLn1Lb0cyuobABO4ePvuzdPTbrvd7bbbx8dvb25uFAqN0HnVV26PLwGY3e3t7atXX/gOIwDAFERd9Fh7R5GOLgBEXQAAoi4AAERdpDCVgGJRMgDnEnXlznXkErWE/E 2X4kZWNFssTheALNFXcIghjMWfl1F7XgBRJTMkpo AdJhzUi/1yGpw cd281376yYjfyE0j8saUxQmZWf0FSckYVLCEZ78x9Znntcesth4Dz1xfUnpZ7kLi8rn/T9qrXdyPrxyjx8v2rtb j8BViNt /e/Oa3v/zVr3/x vVXd3d3F2EPDw hH0LrH68Z qvOdSJb6Vwe jme7ZcfcvMT3/fGX82oOP J6cQTjJTDwOVD6k9iPcxdXlA 6btZ8XyJ1Iescu6tMIn1s6z8E9sfgEW5u7t7/fqrvO8wHt DpnRLvPxJ 7PZWY8nZryjLdj0y6egT mZUWI67S8CjVQOufVn4N8ef2lnysdqY2x3SD5T8rOEugqwZHlPGA B1wRfLF7y hQ/6KnyDewqx6sg/3PVq6XVT cLwBRR12FoyOH/BbewjT/sbcFD60cGqUzZB3Dmgddm8qFsufWnVv4LtlulTCru79LKH DcZDxhbD8oXEKDu6gnepuzfHP 5RCkzPhQpaNrmvwDwJxRV/u6OPxKOfyRzf0n422CzjIpKNjqIdeQg5v4tyn7npJU7jxkVcp8OXWgbH8BTkzJzBEDg63Gk8He1ja0fvtJx8uvjTQTh/zn7l1oVNBaHlZG8t9e3vkwN15utR6uHf/QPr5D6k8o/ynL2 vklk96PRyyv5vMGStC5ZyYn/ikKgX7u/H0HzgtF2/fvXl62m23u912 /j47c3NzYo6YDqjLkYtZ5QPALlub29fvfriar074J4YAFiRq1XnXqSlkJUPAGtxqQgAAERdAACiLpbtVF/FN8WAYgEQdXVfCXrn03JxWlQ5TFY s2dg4fVhIRlzvgBUNOJoejM7wDmH9c53gApR1/BPX3dGY4fPO74sP6wTWt64Ee9dPz6F48QfE5zy4pdYDpHlWeWfUp4p89THo/ZQPcmqV5H9zartoXII1c/DklApRb51GC EeP5rnS9Z YnXE4Dz8vbdm9/89pe/ vUvXr/ 6u7u7iLs4eEh9EN8/fjy49SO/ylleVY6vbmK787qFJdDYjrxBCPlmVsxJq4PiQWVks/E0ydxxyN/dbyPBfmpUj6hRHLLE Ak3d3dvX79Vd53GBtf/0j54kfWuJBQgrn3xwX300v7inYVtfYoJZ32F4HGK88J6sPsZT6k8HPXycqzziqAYnlPGA BV JDxsMjnhkbaxeJ8Qq24MiO8Q3sU9JZDrm3Lo2nq2XpxDM56voAoq4fLgnH/0 Pe1xWTzLw2pzukLhlxmHFEczY6YQG/6kbAAcZTxgbrW3jgePab3AXNb3F6mKvdmXoLE8dXVmn2Horg0MJMDTqajemw5vX9qX6BAK4k4wGhh UISFXYj2pXmE6A8eRbjYKyiG0/DCkMvIO6ajlE0nfuQycs5KZI9IfLHa Md54EtFYp/MhRefyUPqJuTrzhyCRcmgvLyj/4eWZW08i62eVQ246KfV8SIGE8jMkn2OUT2jGilrlAHACLt6 e/P0tNtud7vt9vHx25ubmxk7VDx WiDlT0E9UW0Ajt3e3r569cWVggCG06cF0GtBUVetybqY5riAqgKQ5VIRAACIugAARF0AAIi6AABEXQAAoi4AAERdAACiLgAARF0AAKIuAABRFwAAoi4AAFEXAACiLgAAURcAgKgLAABRFwCAqAsAQNR1Vu7v73PXz/2TReV/geU/6i6svXwAOFVX1a9z19fXA5MamEL1S/gs VlaOUy/X 3gaYwCaWyl7iZC50XZ dJZdC9JZWV7eDq9 U85yo11Dr92Bs3tf0rJamT9yP62M1 xfQNEXZWvo8sPF9bebp5Pu1 2p1l/dbicVy/VSFRRcL50xiKhNEdNpzf/A/saD6nFN9Sb1cj6kf1tZ3517Rtw4lFXWavX2ciGbkPj619fX6ffqXcmfkhhyD10KJ1IPnPLIb4wMT8T9M2M2jcQ36 Cvp saCmrPEfa5XY X/61fcjahVMlndysLkpkf5efeUDUld3TELqqRe4 Q9Fb409SbkM7W9XQfXDnhSflHjoln7nlEMp/QX5G7ZvpfXJUNzBqbG7Uq2ZWeYb tWDHa0V4VdKJJDJlP1DKmT5XOQOMGHVldTUts6ULxTe5F5KCZ1vzXpkKVi7OdkF5hvrM5qozZdsNnR3Do895A7X43chyDCznRhwvMgNmjro2f3 sa3pvU9nVdy2KB vMfn2qG1WPXYYLvwqGYpG1Dw9aS/6H59O4LmBxUVduZ0ZWlHaq95edA2iWmZ/c48V5hlzHdWYJ yhCApamwnxdoXDhuGc 1Ili7OqKnNjxGntH5g25ak2K1k4nMuLwYILovHfvhFzAEqOu7/74pz/ 3z9998c/fffddozr9EurXbFT5ySjtCU/ajznsHjJ 964q6kybukcIpVz219gOb77bnv12ef/4Onpcru93G0vhrdi7XvcdqPWu37jSVbF0axVXqOrlZ/GNATt6TojM2gc/9PY clNf8bRx1nHNzQNRPy4DAnaOmcM2aS99tu5X5Ehd/EngLXSGXKIJ6hXoXyG9nfU8wvgs89 dPH23Zunp912u9ttt4 P397c3Ix3RdRgAQBn6Pb29tWrL65G3YZ7RACAF NGXSItAIAXl4oAAEDUBQAg6gIAQNQFACDqAgAQdQEAIOoCABB1AQAg6gIAEHUBAIi6AAAQdQEAiLoAABB1AQCIugAARF0AAIi6AABEXQAAoi6K3d/fKwQAoNdV9cjj vp6YFIDU0jJ6qibmCWf8fXHLlV6w3HlT277WbFdBU4n6mpc0Rd gbvl5 79ShDBMLM76 3rgZK5vAl7L2c13tKjBd1FUQjXXewx0Wtrtt4usfAqniVin3XvN4051JDWkfjwvqZdfiqcXXf/lV4LW0q2xnFSquhxMv36ynzxjgxKOu3oY4FI2Femsi0VvjT8puB3PvNUPh4/Jvo1ngccmqb0tYDsCcUdfArqbFNuUpGWt3Iy1nd1wml3AIOivGkOOS 7eh9Qemo2pVbGc664kuahB19bTIibFXQZQ2V uj1WOCwL1u/QydX5HzLisdRr07avfla4tA1NUTe6UEXpucoSGztPvt1nCNDXpodzjhqC50fsWXDz9PAYirMF9XKBw57iEP3UyfXi/6/f39Qvbo oir5nnGZJ3nV 5517n cuo5wHlFXfH2 qV1rthpNEtbH9roGJlpRKvtdwvaI8ki63NieqviwLramw6zHHTnNZyGmqPpD782/jV3/cYTjfj6ZVes402kjGZN Xl49iKFUHd9FihxVPXsyyvWc LlHJmhBlipi7fv3jw97bbb3W67fXz89ubmxu0aAEBFt7e3r159cTXqNnzRAgDgxbhRl0gLAODFpSIAABB1AQCIulbLVEPKkxlrS/U1AdaiwriudX0ltzh7U 5X71sIiZmJv5He/gDzNMXSOQlZfH/jF Pel 070x/7A5rLPC/MMLLkYNRxAVHX sKjE2h/41fr9OkuO9Np/DBxObczXxCdhFbo/Nv079ydQ30r/hpEqHzGK7fzOf3b5yYg6hp6ie3te9iEZwXMnYGi owVodBn ibyECpNfyM vDxHzfyKrlhZ50Wj0FLOo r5CZ2PiedpwWyf7fMrUg6bNfcVNW4DBF4g6qpzFQzdz3UuD/2ccnGNpF/WQE/cDka2VSUnxxPZpyRYsTyXcDmZPQ 550Xo51pPMIecjynnaWOd3FoayqroBBB1JV3t5mor6/bhj70X7Xv63JxHvjRSpShqlWdB71duH2puOkuLAtcS0Y5xrBP3UQQGnHvUFfk44JCr7Lw9E9NfjKv3YSzzYpx rNuPlhLHabUD2VnKZ B50f5O4nIOq7cOAWaLujZH3SGRMCL0VWk3svGr2sAo4XiUzJkUb PB6EJy0u6DHJ5O3eiwnUnnKcASo67GtWF1D0oieR4vXglttGLHTOPtRUNk5o29hj iHe8ghtJcWoUx8wKwCiPOkprSqdA5YDY 6 ZkfRXrikVOY6rSzseCjf0asptLKKL0iT WsC h87HsPPUIsjN PX4xReAIp61CX1do1HbK8kiLc/g1Mio8Kz/T9AGMV5610mkXbHwTFcsz9Npj1swCterbZuTR9EPyOVI97yz/3nrS DX3PI2Uf249meV8nDLwEnLBybt47N09Nuu93tttvHx29vbm4W0s/htg9mVDDDBQAht7e3r159saC56afpowKGnI/OU4Biy/oikBYcln8 Ok8BylwqAgAAURcAgKgLWIzQu4HLmazhNCY3ARiiwrgu7zSNd5Xq/KaNDwCvNBLqnBz/TI7gWupq1gwOdd8qiHzDajPse6ORQ9A5aUtB jOWG5xd1OXKOtIM9aENNWaWZ7FCs8a7S1n4uZxyUOrebUbO93jeErcbmrS2Mw7LTX/GcoMzjbqOz7ree5r2lIntf9q0enTa92S5Z29k/dx7ytCsnpF7uNx7wcT5JDmTaKCsHrYrfFbfRt2 lsT9iuSzSjop7UnjrmaCvp9Rz/fO9GuFO5FyA8aKunKjnMaNUWfnTaPVGxWu49ZWLGhuQz9B3GQ1OuaTvDDph4Pey9nQhV1yH1P/FupzMQqXW F6RTJf2KJ2BWUgXb1VbAqUVdjYCgei6nbDUaoeGidsHHqk8mkEqvGAVfSQotH1JtiufuKqi0tar3GPONpXQrVtmF3rZ0 EeEZpkFVy8 oq6Jri6LjcAiH0HLzb/WhDHq8NjnUTxia8cTU340sHjQ0gTtw2bkV1six6jK5ub64lNv3QNRV2HjuJYumeNBaZEnIO17teo3uCkXGN/KPSuhejhBZNN5XkSWryWKrdI LKdKACuy4vm6jqOfKpei6 vr9N7vl5WzGsrhmTweAKejnslOtM7Kdm6VsLG/vY//RioZIReIulIbi5ECr4JmqDH6uCDz959Mub cudypUAsqYW9UsfCKXXY6t /iQm8kzLVT6a9DjprhdvqhckvJjwiSMzTiuK7cUZllozizhuiGnhL2jiqNtCzH7zRF8p/bMXb8Q2O8hSeMqwuShhyvlHqbWLezzrvc5WO3DxXTCQ0S6Dyzysph Pm SZuhJmVbnelXPL65LVLWtCBwYi7evnvz9LTbbne77fbx8dubm5v1XuGmOYfN8gerDoWdsMD0bm9vX736Yt1z08/yZYmx36wGAE7SuqOuuSIekRZoNAByXSoCAABRFwCAqAtYjOVP9DD2pAa5JbPYggJOWJ1xXUaXj3Sp6HxjfNSPkDDe9f54ivNzO19Ota5WnMOlc7KrznpS1t52HoLOSRxqpT9B/uEco64Tm0lhCfnv/CZaY6E2aPlCH34288j0R2Gy87RKgB5pV8va286evFAcViX9CfIPZxp1Zd36tG/3G1FF gR6kbM39x4rZTbCeLfTSOUmumJIvW2fIFl9G3X7KhL3q2I70HmextNvLw tHz9Pc2cNHfXbSp3pV2xYZsk/iLqCrXBvs9jZkBU3Crn3WIkZmD36OZ4AWih2ViFXSr3tvf3YRLtOy86XlPMiMvH6qO1A46zpLYeCn8drM2utPDwyLk4//kn1ReUfVhZ15X4OIrLaGGfX8f3oXA1l3Y0KuU4gkEqvSLmfuIksHxi lGWvoNLOEiUsLVDo7d0Z3t0 6hefevPps2aIuipEA4ln0ah9xZEoMHe7 rSZ8qo/ZT0MPTHsPY8m/gxo4vdbi29Ixl5/pGNU5dar4rirSNXt/HO3joi6asZevU8celv8MaLA0HYjgzwW2C4cD3HQbJ2Dyc6X9Lup3LssRq0Sq8unkItzdlnl1Fpsj0L6GMyXlbP2evodP3570fBS5j2PVMJZ2gchF5x71FUxYitupxqjiQsixftPZg8uj69kWihSKmHFKVIbg99XcZf1csqMMX3DQs7T9PTHvhtce/owu5qj6Q /NpY3nog1nug1/jb9jfFQOr35ibeYh1/jo0pHbWQ7nyG2MyYgW0uQNOR4pdTzxHOh7PxNXF6r3Zix/LPan/iZmNtx3pnPlBltNmmTa7TTr3h8e/PfSKpK/mGlLt6 e/P0tNtud7vt9vHx25ubmxkvUbOcTic2yysAsDS3t7evXn1x9eO/ EdPu932z7bbP9ueZ0FMcM8NAJy5v/jzn1wtJzczhjsiLQBgbJeKAABA1AUAIOoCAEDUBQAg6gIAEHUBACDqAgAQdQEA0O2//PufiboAAEb3 Ed9XQAA4/ubv/nvoi4AgNH95//wl6IuAIApiLoAAERdAACiLgAARF0AAKIuAABRFwAA1f3P//1G1AUAMAVRFwCAqAsAQNQFAICoCwBA1AUAIOoCAEDUBQAg6gIAQNQFACDqAgA4fVfffff9brfb7Xbb7VZxAACM4bvv/9/V7373u6enp5fAS4kAAIzh97///dVnn322T7779XKAAA1f34xz slPfnJ4wviHP/xBoQAAVPf5559fff755y8hl3FdAAAj eyzzy5/dESJTOn /v4csrGQ3QSAef3oRz 6PNa4WE58vXR5FiMCwKlqRlrHl9jr6 vr6 sVXWuFBQDAkl2FQq6Xn18Cr8OvkRDtEPQcr3wcCaUs78xDSjqNRIq3G4nketOJlEPKJorz2S6rl19TjktKuR0Wvvww5LgAwFn7 PHjN9988/XXX79///7u7u7i4uLh4eHiSOPXtoeHh N1Dj H0uldHs9A52qhn9OT7dyv3PxHsjG83Ary2Zv 8TqJxZ57XHrzDwAn7 7u7v3793W CNTZpZHYz9HubmksGam/JDfZ4/6/6mmOpDf94xXGyIy LgA4uBo19dyxVqGnmQXpdEYA7Wdk0 zX0tKveLycQgAwf9QVGZsV0jmMLJROZBBVKK46DHgaEnsV7FeuWbqIyo6XUwgAEl0uLUO5L06 vGuZu4l1vZ4JAJxm1HUckfS wHhYrXiF9j9FQqL28vtPetMfGGZ1/vkYaQ7ZRGPl4uNSsF J5TP9PHAAsBDdTxhzh0B1PuxrLOz8eRMeiX8I EJ/G5oxIZR ynYjwV/vfhXoLbfcfLb/tuy4tPerXSUmKB8AOCUXHz9 PHyH8cOHDzc3NwWdHAsZh2SY0RKOCwDQcHt7WXX16tdwdy 4QAAGZUIeqaMdwRaSkcAFiLS0UAACDqAgAQdVXiHbfzLGHHHQBR1w8XxUVdF12kz7M8HXcATjzqepl0wGRLp8GwegBYgqtQyHW4YPdO xSaN vlh85PJYa n9g5E0RjcvnQtwJTlkd2oXO7vfkfkn7u8oJyjhda459y5z87geMOAJP6 PHjN9988/XXX79///7u7u7i4uLh4eHiSOPXttD6Dw8Px/90vPx4YefylGxEtjtZ/gemX2t5Zz7jOUwvz1M97gAwmbu7u/fv3487mj7lazZjd05k5SH3b8fIT8H6S vXWcVxB4CJLWtu txhZJ3r535EMnG7oSdZKX8Yys8Yw bWGG3MddwB4EyjrvY4oeII4zDAKOUaXHG78fXb REfzHjcAWBipzxL6tJew1z4a6HHeVv1u6tevwVgNVFX4 qb1WfQuNT1XvlCKxRcMqtEDEO2OzDNrKIYKaR4OfS5B30Vx31p888BcIauIlffTfJQ7uMZARpv77cnCwitH0mnM0vtbcWXF S/d/3c9IfkPzefm jkC6FDnB5vrf24A8DELj5 /Ljb7bbb7Xa7/fDhw83NTa2kC7pMWI7iw e4A0DD7e3tl19 eaUgOA6YDj LnACgrhGjLpft1alyyBx3AOh0qQgAAERdAACiLgAARF0AAKIuAIDz8ubNG1EXAMDofvrTn4q6AABG9/T0JOoCABjdfr8XdQEATEHUBQAg6gIAEHUBACDqAgBYkP/2V38l6gIAGN3f6usCAJjEn4u6AADG9/m/FHUBAIzun/yrfyPqAgAY3b/91/ 0ZtR1f3 /2NQ42wJXkZQD6i0soeL9i3/8fNm5sYaBWR/1tBErTFMOofQnK//ZM7DM u9aWDdjc 0ow2 AAAAGUElEQVTX0upJKD9jN ZVLjprv1IUXH9nrLfasSz/cL /6vyH6 vrguQ6/ r6 trNCicZdqScJsX1PzF9TsPS2snp89Oo8Odc/192XAuwhKNQ3T4UdaUEho08vfxTYkZD6RyWp6RzWLm96Ug y/JzvPzlZGhnNbS8IP2sIq1YDp2HIJR ZHluOfTubKgBarfU8fSHHN9I/axe34akH796hepte/1IPY8c96yrZtl5cchVO/3jjUbWzz3vCso/t/4PL5 C5WWNf5V2pnjrVfY3sXKG6nOk3Ug/j8qi0vTzcezrV 51al3X2cjC9PyEoq7Nx48fv/nmm6 //vr9 /d3d3cXFxcPDw8XXRrL26uV/eHh1 PlDw8PodR6N9qbz8T1I8sbWe1dnpV YrbHKIfO/Gcd3IJy6D3iw tV7nHpXT roMrq/xj1uUo5zHjelZ1BjR9yz7ta59EY9WR4O5PVpFQpn6zNVWxXQytUr59Z51FWBqqcj7WuX8N3Z HX2YHXl053d3c///nPr9Jj0il7O2fsb098bFS9T3IJncm18lBQhtV3/zjB0LPvJR LMfKW 7cTn/InU Cj7kti4nOV5xjbrVjnZ3lsN2W7OiSdpZ3va7nOZqX54cOHvHFdtSKhcxvpZWRb/MFQej9/3dZzFfW5rNzOTVZ9qPKqSnthb3Bf6xWZzuXxB6/F V9y/Swoz9lPoikzkFI uU8GXWcH tnPfnZVXGWH7OG5XT9cL4/LYSExRG59jjy8r7IvvemLvWY5H3sHxo3XDpSNZWzXk9y 3rWc1wXleVZD1JfWx Y6 8IsqcxwbrSfIHe Iz1qR9eQzM Sfme5sfG21zLqSd3tjpT/9Bwer mkY/6oq2ItnH5WmFnO9t70T nErnJMB4ZcWZtLX7l3Ep0q89sdJxJPMCszvXkb75LZO/NQ8aYHhlwj1ZPqSfWeU3NN7DSkfs7SruYGXgUVbIGN dKi4XO zmY8YWw8Aek84VMmF2j87fFo/VD6KbnqTGeT0OuYkp/NgN7LsvRzR0sML4fc9CPLOx W9e5v3bvYrOOeUt9Cb4ZHtptV/wvSz92v3uNS67xLSWfs866sngzfr4LtVmknK5Zn5KX68dqZKdvt9EeN7XXqXr9yy3/69r/WdWpF19ms87HAxcePH3e73Xa73W63Hz58uLm50QHIwJuMk3zcM/YsjmaJBM0aJ z29vbLL7 8UhAwxr340tIHciMt5yPVibqoH53YNUUHzndo8w4jAICoCwBA1EWIyV0AAFFXtRBKaAUAiLpmVjYGUxgHAKftqjcCaMzimP4ZstD6kXSyZo8smN od5bCTd8Ur5u Kew6p1zr3d/ORIbEcADA4qKu3//X/7h73u e99vn/ebf/ad4NBP6OR54Jf481yyUkTnBO7MRWn741/j3BDu3GylYs/MBwAn427/ y8vNZn/0X4 Cb7wPT6fxFdI1fkd9yLaEXABwEvZXm f9Zv/y3/Ms0UDZR6bKNhRKZFFjqqrsLACwsKDr Wr/SUJX1 odHu1tWp90nTG62gQ BS32AoATiro2V5vN86e ruWGXZ1joY6/G5/VWRUfmDVLILj8fAIAw6Ku58vN8/7Tf8/V06/y5K4daR3HJff394lxSWJmJn7aeP/JXBkAAKbw/Nwxc0Q7silOP2umibLtpmcvlH58u6FRVp3L45NKRKLJzd9/d9LMEQBweq72z0 bw9Cu6JW 7PLf/qveZ2rxhWO8DxhPM/2vauVfpAUAJ2a/f776YVDXfn3D6VfdJ6RPCwDOKuy62mz2ydN1ZUcVEwQuqy5/kRYAnE3UtTnq6zqHqSMAAObxfLV/ftrvN/v9fv8s6gIAGMXflSKQAATODTF4GeVzmaHgBgHfbPl5vNp0Fdoi4AgLGirv3V5vl5s99vnjcb47oAAEbyvL/c/F0f13l8/hoAYA77zUtf1/N s9fXBQAwmufnq6MJUkVdAAAj2X ar t5v3lWHAAA43h vtzsD2O69HUBAIxkf/nDRxgFXQAAYwVdm6vN/vnvOrrM1wUAMFbU9Xy13z/v9/v988Z3GAEARgu6no9mSRV0AQCMFXbtr34YSi/qAgAYL r65//jt7vdbrvdbrfb//PhgzIBAKjun/31/7pUCgAAE/j/eEalGduQYX4AAAAASUVORK5CYII=[/IMG][ATTACH=CONFIG]280176[/ATTACH]

---

### Post by wbucky on 2018-06-28
/usr/lib/ubuntu-release-upgrader/release-upgrade-motd
actually calls
/usr/lib/ubuntu-release-upgrader/check-new-release

If you run "/usr/lib/ubuntu-release-upgrader/check-new-release", that's the script that fails with the error message.

This bug was reported and just fixed. However, it looks like it is merged into the 18.10 branch. The latest 18.04 Bionic update-manager is v1:18.04.11.2
[https://launchpad.net/ubuntu/+source/update-manager/1:18.10.3](https://launchpad.net/ubuntu/+source/update-manager/1:18.10.3)

I'm not sure if it's possible to install update-manager 1:18.10.3 without upgrading to 18.10 Cosmic. You could make the 1 line change that was suggested in the original bug report:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1771914](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1771914)

---

### Post by d3atiq on 2019-03-07
Hi,

Just installed the latest Ubuntu server 18.04.2 and ran into this. A little investigation showed me the message actually is recorded in the cache ([COLOR=#000000][FONT=Menlo]/var/lib/ubuntu-release-upgrader/release-upgrade-available[/FONT][/COLOR]). All I did to make it go away was: sudo rm [COLOR=#000000][FONT=Menlo]/var/lib/ubuntu-release-upgrader/release-upgrade-available


[/FONT][/COLOR]

---

### Post by karimakela on 2019-03-10
> **d3atiq said:**
> Hi,
Just installed the latest Ubuntu server 18.04.2 and ran into this. A little investigation showed me the message actually is recorded in the cache ([COLOR=#000000][FONT=Menlo]/var/lib/ubuntu-release-upgrader/release-upgrade-available[/FONT][/COLOR]). All I did to make it go away was: sudo rm [COLOR=#000000][FONT=Menlo]/var/lib/ubuntu-release-upgrader/release-upgrade-available
[/FONT][/COLOR]

Metoo, just yesterday. As far as I know, the server was always connected during the installation, I do not need any proxy, and wget can fetch the URL perfectly well (certificate valid).

I also deleted the file to get rid of the message.

---

### Post by no1san2 on 2019-04-07
Any reason to remove the message? (as mentioned above)

---

### Post by peter.h.m.brooks on 2019-04-21
I'm having the same problem:

> # do-release-upgrade
Checking for a new Ubuntu release
Failed to connect to [https://changelogs.ubuntu.com/meta-release](https://changelogs.ubuntu.com/meta-release). Check your Internet connection or proxy settings
No new release found.


I've tried removing the file [COLOR=#000000][COLOR=#000000][I][FONT=Menlo]/var/lib/ubuntu-release-upgrader/release-upgrade-available - but this makes no difference.

My DNS is fine.

I'm wanting to install 19.04[/FONT][/I][/COLOR][/COLOR]

---

### Post by neil.borromeo on 2019-04-28
Could this be an SSL issue?

I see similar discussion here
[https://askubuntu.com/questions/1072819/failed-to-connect-to-https-changelogs-ubuntu-com-meta-release-development-che/1086496](https://askubuntu.com/questions/1072819/failed-to-connect-to-https-changelogs-ubuntu-com-meta-release-development-che/1086496)

---

### Post by axelitusmx on 2019-08-28
I started having this issue today also. When I connected to my server it showed the message:

```
[COLOR=#000000][FONT=&amp]Failed to connect to https://changelogs.ubuntu.com/meta-release-lts. Check your Internet connection or proxy settings.[/FONT][/COLOR]
```

The message is stored in the file [FONT=courier new]/var/lib/ubuntu-release-upgrader/release-upgrade-available[/FONT]

It seems that when the connection can be re-established to check the changelog, this file is not cleaned up properly. So, after the first time it cannot connect, the message is stored in the file and never erased so it will always show up as if it cannot connect (when actually it is connecting).

Just run the following code to clean up the file manually, after this if there's no connection issue the message will be gone:

```
sudo truncate -s 0 /var/lib/ubuntu-release-upgrader/release-upgrade-available
```

---

