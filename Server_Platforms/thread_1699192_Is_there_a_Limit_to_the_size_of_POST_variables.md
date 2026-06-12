---
title: "Is there a Limit to the size of POST variables"
date: 2011-03-03
forum: Server Platforms
---

### Post by jasonbrisbane on 2011-03-03
Hello All,

I have a problem with a PHP/Apache program.

The website creates a RPG character through a traditional Wizard. It calls itself with a hidden variable being the page number and tests which page and returns the page data with the page incremented.

Each page should be treated as a seperate page and so would be unique.
I am echoing the contents of POST to the top of the page and so I can see variables being returned.
When I get data from an Ajax query from page three it saves the data (23 post fields of no more than 25 characters for each field).
Page four does the same but with less fields - but it is NOT returning the data - only four fields being those that were originally posted.

I cut/paste the function from section three to section four and changed the displayed text and the names of variables to test so there are no code errors, since page three works and is saved to a database.


So the only option is that there is a PHP or Apache2 issue when POST variables are returned?
I am completely out of ideas as to why this would even be an issue or how it could possibly appear.

Is the number of variables an issue? This page is less than the previous page.... And the form is POSTed...


Has anyone experienced this before and does anyone know why it might occur?

PS: I am getting NOTICE errors from PHP being the POSTed variables that are not displayed/returned... I used: 

error_reporting (E_ALL ^ E_NOTICE);

 to stop these form being reported but do I need to test each one?
PPS: Using If Isset($_POST['xxx']) does NOT allow that variable through...

What am I doing wrong?

PS: I have the default Ubuntu 10.04 Apache2 with all the ubuntu 10.04 updates...

---

### Post by bsntech on 2011-03-03
I haven't ever run into any problem with a maximum of POST variables in PHP.  But, I don't have huge amounts either.

I've created forms where files are uploaded via a POST form as well - no problems there either.

Might need to provide any more information that you can for us.  Does it seem like all of the POST output is appearing for the first X number of variables - and then none occur after that?

If so, you may have some PHP code errors - in that the PHP code is running up until the point of failure - then it dies.

Brian S.
[http://www.bsntech.com]("http://www.bsntech.com/bsntech-blog-mainmenu-321/computers-mainmenu-281/")

---

### Post by wongo888 on 2011-03-03
I'd bet that there are logic errors in your code. Get someone else to read it.

Don't turn off PHP notices/warnings/errors until your code works, until then you want to hear what PHP is telling you. Read your Apache error logs.

The max size of POST and GET is configurable. You can POST megabytes of data no problem if your Apache is configured for it. PHPinfo reports these limits (see post_max_size).

[http://httpd.apache.org/docs/current/mod/core.html#limitrequestbody](http://httpd.apache.org/docs/current/mod/core.html#limitrequestbody)

---

### Post by jasonbrisbane on 2011-03-04
Figured it out...


IN my php there is the base form, which has a hidden ID, hidden page number and a field that changes on each page. ON this page is is class (profession). When you choose a profession from the radio button choices then it does an ajax call to a background.php server program which returns extra form fields.

These extra form fields are the ones that are being ignored. ***The browser simply seems to be returning the initial form values and ignoring whatever is on the screen at the time the forms submit button is pressed***.

So I will simply install a backgrounds part a and backgrounds part b to the wizard screens. Yes the screens increase by almost double, but it works.

There are no errors in either php or apache. I used the w3c validator to ensure things were right. The script wil be hosted on other peoples servers and I wanted them to NOT drop memory, or crash at inopportune times. Using the Validator helped me clean up my php no end!

---

