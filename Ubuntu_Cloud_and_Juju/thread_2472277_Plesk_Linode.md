---
title: "Plesk Linode"
date: 2022-02-22
forum: Ubuntu Cloud and Juju
---

### Post by hackingv01 on 2022-02-22
I am running Plesk on my ubuntu server while it does a great job it does require a license can anyone recommend any alternatives to Plesk. I am using Plesk as it's easy to migrate to a new server.

The website I am working on that will supply Website design and also hosting I want to get everything right before I start to mess with clients' data. Is there anything I should watch out for while running Plesk. I did have to repair a couple of times due to config disappearing in the past but everything has been fine for a while. 

Is it worth paying for Plesk these days or just running Ubuntu Server natively?

I plan on hosting over 10 sites on the server I don't want recommended cPanel.

---

### Post by CharlesA on 2022-02-22
That all depends on if you want the customers to manage their own stuff or if you want to have to manage it for them.

There are several different front ends that you can deploy, with cPanel, Plask, WHM (works with cPanel), DirectAdmin, and I'm sure there are others out there.

---

### Post by SeijiSensei on 2022-02-23
As Charles says, it depends on who needs access. 

I run Linode servers running stock versions of CentOS. I manage them via ssh. I've never used a dashboard app for this purpose.

The only system I use for development, aside from writing my own code in PHP, is WordPress.  That requires some attention to make sure you upgrade when needed to avoid security issues.

---

