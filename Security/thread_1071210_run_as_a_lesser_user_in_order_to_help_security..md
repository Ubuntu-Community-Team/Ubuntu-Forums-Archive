---
title: "run as a lesser user in order to help security."
date: 2009-02-15
forum: Security
---

### Post by sulekha on 2009-02-15
Hi all,

This is what i have read in the book "Linux Administration a beginners guide by Steve shah and Wale soyinka"


 some applications that are started by the root user give their permissions to run as a lesser user in order to help security. 

Ex: 

The apche web server,must be started by the  root user in order to listen to port 80(only root users can bind to ports lower than 1024), but it then gives up its root permissions and start all of its threads as lesser user. (typically the user "nobody" , "apache" , or "www" )


 can any one give more examples for this ?

---

### Post by HermanAB on 2009-02-16
Use ps on a running system to see how it is done:
$ ps -eo euser,ruser,suser,fuser,f,comm,label

Cheers,

Herman

---

