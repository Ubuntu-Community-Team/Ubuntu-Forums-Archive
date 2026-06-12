---
title: "Setting Environment Variables for D tango"
date: 2010-01-16
forum: Virginia Team - US
---

### Post by CSdavid on 2010-01-16
I was wondering if anyone could tell me how to set the PATH variables.  I went into .bash_profile but its empty.  I am sort of new to Linux.  I use it at school but usually everything is already setup correctly.  I really need to get this set up I have projects to write in the D programming language using the tango libraries and I cant seem to set up the environment path variables correctly.  

thanks

---

### Post by CSdavid on 2010-01-17
I figured out how to set the PATH.

sudo gedit /etc/bash.bashrc
then write at the end of the bashrc file

export PATH=$PATH:/some/path

baschrc and bash_profile are the same thing but cetian bash shells used bashrc rather than bash_profile

---

