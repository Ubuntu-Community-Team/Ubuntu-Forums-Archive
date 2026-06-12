---
title: "Deploying Ubuntu Workstations in Corporate Environment"
date: 2013-02-26
forum: Security
---

### Post by jla0 on 2013-02-26
We are starting to deploy more and more Ubuntu 10.04 workstations for our employees but need a better way to lock the machines down similar to how we can use Group Policy to lock down a windows machine. We are using 10.04 because the software we use requires that version. 


Below are a few of the immediate questions i have.

We are using Likewise enterprise for authentication with active directory and to allow us to run scripts against a machine.

1. How can i allow a user to read USB storage or CDROM drives but block them from writing to these devices unless i explicitly grant them this right.

2. How can i prevent a user from changing the root users password if i grant the user sudo permissions?

---

### Post by chadk5utc on 2013-02-26
This can be done with user/group management. Have a look at the following links for more detailed info.
[http://www.debianhelp.co.uk/userandgroup.htm](http://www.debianhelp.co.uk/userandgroup.htm)
[http://howtoxyz.blogspot.com/2007/11/limiting-power-of-sudoers.html](http://howtoxyz.blogspot.com/2007/11/limiting-power-of-sudoers.html)

---

