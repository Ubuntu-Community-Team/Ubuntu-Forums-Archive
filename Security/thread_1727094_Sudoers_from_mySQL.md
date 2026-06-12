---
title: "Sudoers from mySQL"
date: 2011-04-12
forum: Security
---

### Post by santium on 2011-04-12
This may be a stupid (?) question, but does any one know of a patch for sudo that allows the sudoers information to be pulled from mySQL?
I run multiple servers with multiple people working on them and would like a one-stop update of permissions. 
Yes, I could use rsync or the like, but I'm just wondering if this has been done, or could be done.

(Sorry if this is the wrong forum, I'm kinda new around here, posting wise and this seemed to fit. Feel free to move it if it's not)

---

### Post by BkkBonanza on 2011-04-12
I've never heard of a mysql backend for sudoers, though probably a script could be made to generate the file from mysql. I don't think it's a very good idea as it reduces all the root permissions on your machines to a mysql password - and depending on what other apps you have using your mysql db that could lead to many vulnerabilities.

A better approach would be to explore [**pssh**, **pscp** and **prsync**]("http://www.linux.com/archive/feature/151340") - Parallel versions of the common tools, to update multiple servers at once. Those tools may come in handy for many admin tasks.

These are in the repos named as package **pssh**.

---

### Post by bodhi.zazen on 2011-04-12
> **santium said:**
> This may be a stupid (?) question, but does any one know of a patch for sudo that allows the sudoers information to be pulled from mySQL?
I run multiple servers with multiple people working on them and would like a one-stop update of permissions. 
Yes, I could use rsync or the like, but I'm just wondering if this has been done, or could be done.

(Sorry if this is the wrong forum, I'm kinda new around here, posting wise and this seemed to fit. Feel free to move it if it's not)

I would use a well written sudoers file + rsync. I think that would be simpler and more secure then mysql.

---

### Post by SeijiSensei on 2011-04-12
If you're trying to centralize authentication for a number of Linux users, you might want to look into [NIS]("https://help.ubuntu.com/community/SettingUpNISHowTo").  Changes to the passwd and group files on the NIS server will apply to all other machines using that server to authenticate users.

If you're really hardy, you can try setting up [OpenLDAP]("https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html").

---

