---
title: "Package downloading &amp; updating on two machines"
date: 2008-07-11
forum: Repositories &amp; Backports
---

### Post by mié tonda wè on 2008-07-11
Hi all, 
I'm looking for tips to enhance the package downloading & updating workflow between my 2 ubuntu boxes, let's call them a and b. 

I want to download new packages only once but have them installed on both machines.

For now, what I've been performing is

1) on machine a:

cd /var/cache/apt/archives/
rename 's/%3a/:/' *.deb
dpkg-scanpackages ./ /dev/null | gzip -9c > Packages.gz

2) on machine b:

cp /etc/apt/{sources.list.machineA,sources.list}
apt-get update
apt-get dist-upgrade
cp /etc/apt/{sources.list.internet,sources.list}

While this method works, the contents of 
/var/cache/apt/archives/ keeps growing, which is quite problematic.

Then I need a script that would, either delete the packages in machineA:/var/cache/apt/archives/ after they've been installed in machineB, or scans through the contents of /var/cache/apt/archives/ and delete all but the most recent packages.

What do you think ?

---

