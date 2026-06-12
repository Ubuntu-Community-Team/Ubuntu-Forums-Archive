---
title: "how to access splunk root  files with snare"
date: 2008-11-10
forum: Security
---

### Post by Visa on 2008-11-10
thats the question my splunk logs are in the ownership of root 

i need to acess then with the snare file directory gui 

its not happening files path isnt correct 

thats my biggest problem 

os ubuntu 8.10 with only ossec splunk and snare installed plus updates 

id also like my ossec agent .log windows file inot snare as well but thats another story 
 

ty 


Visa

---

### Post by cariboo on 2008-11-11
For any operation the requires root permissions preface the command with sudo. For almost all file operation I prefer to use Midnight Commander, it is available in the repositories as mc. If you run mc as root:

```
sudo mc
```

You have access to everything.

Jim

---

### Post by Visa on 2008-11-12
its ok ihave to use epilog to access non splunk files as i have found out :   ) 


:  )

---

