---
title: "Error message: “can not find '__main__' module in ''”"
date: 2016-09-19
forum: Server Platforms
---

### Post by padelis94 on 2016-09-19
Good evening! I am new to linux (ubuntu). Following instructions from the Internet to install the "Darwin calendar server", after the command &#8220;bin / run -n&#8221;, displays the error message: &#8220;/usr/bin/python2.7: can not find '__main__' module in ''&#8221; . In a related search for that error I have noticed that occurs in various situations. Is there any idea (or link) about that case? Thank you very much!!

This is the website with the code (scroll down):
[https://github.com/apple/ccs-calendarserver](https://github.com/apple/ccs-calendarserver)

---

### Post by ian-weisser on 2016-09-19
Please show us the complete output, unedited.
Python errors usually include a lot more helpful information.
Please use [code] tags to contain the output.

---

### Post by padelis94 on 2016-09-20
Hello!! 
Thanks for the answer!
I don't know what the [code] tags are. 
The exact output is this:


name@Personal:~$ cd CalendarServer
name@Personal:~/CalendarServer$ cd ccs-calendarserver
name@Personal:~/CalendarServer/ccs-calendarserver$ bin/run -n
bin/run: 471: [: true: unexpected operator
bin/run: 104: [: Illegal number: # 1 "<stdin>"
bin/run: 109: [: Illegal number: # 1 "<stdin>"
bin/run: 562: [: true: unexpected operator
Using /home/name/CalendarServer/ccs-calendarserver/.develop/virtualenv/bin/python as Python

Starting server...
/usr/bin/python2.7: can't find '__main__' module in ''
name@Personal:~/CalendarServer/ccs-calendarserver$

---

### Post by rahuldate on 2017-08-02
Hi,
Did you resolve the error?

Would be happy to get some help!

---

### Post by cariboo on 2017-08-02
@rahuldate, you'll probably get a quicker response, if you create a new thread, including any error messages, and what you have done yourself to solve the problem. This thread is almost a year old, and the original poster hasn't been back since he made his last post.

---

