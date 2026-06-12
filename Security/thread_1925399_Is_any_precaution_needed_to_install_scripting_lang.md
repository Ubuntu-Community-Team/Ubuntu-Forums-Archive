---
title: "Is any precaution needed to install scripting language and GUI toolkit?"
date: 2012-02-14
forum: Security
---

### Post by arroy_0209 on 2012-02-14
I am using ubutnu 10.04 and planning to install sage (math) program. I may need to install Tcl/Tk libraries with this. However I have no idea whether installing such scripting language (Tcl) and GUI toolkit (Tk) should be done with security-issues in mind.  Indeed there is at least one website which lists security vulnerabilities for Tcl Tk and I fail to fully understand these technical issues. Can anybody please suggest how I should proceed? Thanks.

Edit: It appears that sage can be built from downloaded source file without using root privilege i.e., sudo command is not necessary. Does that affect the answers to my question?

---

### Post by SysTheron on 2012-02-14
It should not be dangerous to install a scripting language. The scripts are executed with the privileges from the user who run it. And if you don't want to use it for server-technical stuff there is nothing to fear. Just look into the scripts you run(but this you should do with every script)...

---

### Post by arroy_0209 on 2012-02-14
Thanks for the reply. However what do you mean by:
> 
Just look into the scripts you run(but this you should do with every script)...     

How does one "look into" the scripts? You mean to understand the script program? What command should I use for that? Also I guess trying to understand the entire program would be a huge task. Are there any simpler methods?

---

### Post by SysTheron on 2012-02-15
Simply open the script in your favorite Texteditor(gedit, nano, vim).

---

