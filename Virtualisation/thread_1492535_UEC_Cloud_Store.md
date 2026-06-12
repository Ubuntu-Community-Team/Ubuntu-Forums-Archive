---
title: "UEC Cloud Store"
date: 2010-05-24
forum: Virtualisation
---

### Post by wcorey on 2010-05-24
After installing the cloud cluster components and the cloud node components and you can get into the store and suck down select images, specifically 9.10 64bit. Where in the cloud does it know you have downloaded it, as opposed to it's available for download????

I had to reinstall the cluster component (easiest way to provide a new public ip address range. However I no longer have the 9.10 image I downloaded and was able to deploy however the store web app thinks it is still available locally.

How do I reset the store?

Thanks,

Walt

---

### Post by prateek4tech on 2010-06-11
I also need an answer to this.. can someobody pls help

---

### Post by wcorey on 2010-06-12
I actually did find the answer to this. 

[https://answers.edge.launchpad.net/ubuntu/+source/eucalyptus/+question/112156](https://answers.edge.launchpad.net/ubuntu/+source/eucalyptus/+question/112156)

In short the answer, from Torsten Spindler was:

"The image store is handled by the package python-image-store-proxy. I
have never tried this, but believe that when purging the
python-image-store-proxy and re-installing it, it should have a clean
status again."

This worked fine. However, while it did re initialize the store it shows that the store is a static entity. One would hope it was dynamic in that once cleared I did pick up 10.4 image(s). It would be nice if the store would grow and have, perhaps, non ubuntu server images, perhaps ubuntu desktop or U10.4 server instances with tomcat6 and mysql or jboss 5.1 and mysql as, apparently, 10.4 broke vmbuilder and ec2- utils to build/modify images. 

I was meaning to circle back to this question on the forum and mark it as solved, as I did the question I asked on launchpad.

---

