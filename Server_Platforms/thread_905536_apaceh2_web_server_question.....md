---
title: "apaceh2 web server question...."
date: 2008-08-30
forum: Server Platforms
---

### Post by hockey97 on 2008-08-30
HI  I just found out that on my website it's not done yet but I notice that if you read the source code of the page you can find the direct url to my scripts which when I put it in the browser I notice I had access to it. It would show the whole script.. this means the users can read my javascripts and html and css codes.

How can I denie  users/clients from downloading or getting a hold of my scripts???

I already config apache to not show a list of dir ect..ect..

Is their a way where I can lock these files but yet they will still be runned on the website like the clients could still use the websites but just can have access to the script files directly.

just want to know since this is a security risk in my terms and would like to not allow users to see my scripts or even download them cause if a hacker gets a hold of these scripts they can easily hack my website.

---

### Post by windependence on 2008-08-31
There are ways to make the links hidden but I forget how to do it. ;)

That being said, your doc root files should not be writeable by anyone but root. You should set your permissions so that others only have read and execute acces and the dorectory should not be owned by the Apache user. Most times it is owned by root and the root group.

-Tim

---

### Post by hockey97 on 2008-09-01
no the permissions are set for my user.

I don't know... I think I did had root before but it caused problems with Apache not finding anything.

Well what permission should I set it too???


I don't want people going on my website and then looking at source code and seeing the url of the javascripts and then just copy and paste that url to the browser to then be able to download the script.

ok so what is happening I have javascripts which when  you check page source meaning the html doc you can see the url to my javascript.

that url if you type it in the address area in the browser you will get a prompt asking if you want to open it or save it to your pc and if you click save  you download the file to your computer.

I want to show a denied access error or somthing. I want to block anyone from getting the scripts but still want the scripts runable.

it's just not secure allowing anyone reading the source scripts of the website.

can you tell me any more on how to do this??

---

### Post by leg on 2008-09-01
You can use [.htaccess]("http://en.wikipedia.org/wiki/Htaccess") to deny access to the folder from outside the host. I have given you the wiki page but do some more searching and you will probably find what you need.

---

### Post by mbeach on 2008-09-01
since the browser runs the javascripts, and needs the css in order to display your site correctly, and obviously needs the html in order to pull it all together and hold content, you need to send it all to the browser.  There's not a whole lot you can do to hide your css, html, and javascript.

You may also be surprised to know that hidden form fields, unwritable form fields can all be seen/written (most easily with firefox add-ons) - this is why it is important to create your application in such a fashion that having access to the javascript is not dangerous.  Leave all the important validation, processing on the server side (php/perl/cold fusion/python etc...)

you could take the approach Google seems to use and have non descriptive function names, very short variable names, and push it to the client all in a single line.  This makes it more difficult to easily see what is being done, but not impossible.  View the inline javascript at their home page for an example.

---

