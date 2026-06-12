---
title: "installing multex-bin fails"
date: 2005-04-26
forum: Repositories &amp; Backports
---

### Post by GoldBuggie on 2005-04-26
Hi

I've been trying to install multex-bin cause i want a good complete latex package. But there seems to be some trouble in setting it up. I've tried installing it via synaptic, kynaptic or regular apt-get. After the first installation I did a "apt-get install -f" and the following message appears...

sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up multex-bin (0.8.1-7) ...
mktexlsr: Updating /usr/local/share/texmf/ls-R...
mktexlsr: Updating /usr/local/lib/texmf/ls-R...
mktexlsr: Updating /var/lib/texmf/ls-R...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN...
mktexlsr: Updating /var/cache/fonts/ls-R...
mktexlsr: Done.
Make format files of multex-bin. This may take some time. ...
The format file of `multex' is built successfully.
The format file of `mullatex' is NOT built successfully.
Visit `/var/lib/texmf/web2c/mullatex.log' for details.
dpkg: error processing multex-bin (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
multex-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)

There is no trouble using remove afterwards to get rid of it. But sadly enough I don't know what to do to get it to install correctly.

I asked this same question in the kubuntu area but nobody has tried to solve the problem. I'm hoping someone in here could answer what the problem may be since it is not only me that has it.

---

