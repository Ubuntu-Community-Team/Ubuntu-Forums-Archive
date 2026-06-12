---
title: "Problem accessing html pages......"
date: 2014-06-09
forum: Server Platforms
---

### Post by dusan3 on 2014-06-09
Hi everybody,

I have created some example of Apache Default Page (replaced with my html page) and on that page i have some drop down menus that navigates to some html.links.
When i try to click on some of that links i got error like this:

[COLOR=#000000][FONT=Times New Roman]The requested URL /computers-c-67.html was not found on this server.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Additionally, a 404 Not Found error was encountered while trying to use an ErrorDocument to handle the request.[/FONT][/COLOR]
[HR][/HR]Apache/2.4.7 (Ubuntu) Server at localhost Port 443

And i cant figure out whats the problem.I installed openssl also for [https://localhost](https://localhost) and that works fine,but when i try to access html page like in upper example i got error 404.
I port forwarded ports 22,80,443 on my router.
Can somebody help me with this?
It would really mean to me.

Thanks in advance.

---

### Post by dusan3 on 2014-06-09
Any suggestion? Anybody?

Thanks.

---

### Post by SeijiSensei on 2014-06-09
The URL "/computers-c-67.html" points to a file with that name in the root directory of the website.  Is that where the file is located?

That URL is equivalent to [http://www.example.com/computers-c-67.html](http://www.example.com/computers-c-67.html).  Does that file exist?

---

### Post by dusan3 on 2014-06-09
yes ...it exists ... but dont know whats the problem ....

---

### Post by rahul4557 on 2014-06-09
Check on main index.html file if the hyperlink to the page computers-c-67.html is correct. it should include location ie folder names if it is located in a seperate folder..

---

### Post by dusan3 on 2014-06-09
Hyperlink is ok in index.html .... but still i got error 404 ....

---

### Post by rahul4557 on 2014-06-10
error 404 means it cannot find the specified page, so i feel there  should be something wrong with the location of linked file ie.  "computers-c-67.html"..
check whether you are using a "/" before the folder name, where file "computers-c-67.html" is located.

---

