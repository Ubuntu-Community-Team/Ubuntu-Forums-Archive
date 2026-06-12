---
title: "Tomcat 6 + Python CGI"
date: 2010-04-14
forum: Server Platforms
---

### Post by danandjan on 2010-04-14
Hello, I used to run a Tomcat 6 server on a winxp machine at home so that I could learn Java and Python CGI scripting.  I will eventually run Apache, but I just don't have the time right now since I am now trying to learn linux/Ubuntu.
Anyways, I made a very simple web survey application using Python CGI scripting on that winxp machine with Tomcat 6 server and that survey application's been working fine with no problems.  Well my winxp machine over-heated and took a dump.  So I bought a used laptop and installed Ubuntu 9.10 to give Linux a try. So I am completely new to Linux.

I then installed Tomcat 6 to my new Ubuntu machine, ported my Python web survey code over. Everything seemed to work ok after some headaches (found out I couldn't run Tomcat server on port 80 unless I was root user, etc.), except for some reason, in my main survey Python script, Python's urllib.urlopen() method doesn't seem to
work right on my Ubuntu machine.  However, the exact same code ran fine on my winxp machine.


Here's the code that I am referring to that doesn't appear to work right on the Ubuntu machine:
```

page = urllib.urlopen('http://myhomeIP/python/www/HasVoted.html').read()
    print page

```

This code suppose to just forward a client to a HTML page and display the contents of that HTML page ("HasVoted.html"). But for some reason, on the client's browser, all they see is a blank page.  I right-mouse clicked and view the source on that page.  What it showed is 
just a empty HTML page, so apparently "something" wasn't parsed right or perhaps nothing at all.

This is what the view source option showed from the client's browser:
```

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
<HTML><HEAD>
<META http-equiv=Content-Type content="text/html; charset=windows-1252"></HEAD>
<BODY></BODY></HTML>

```

So pretty much, it is indicating that nothing was sent back for some reason.

Here is the contents of HasVoted.html:
```

<html>
<head>
<title>Already Voted</title>
</head>
    <body>
    	<h4>Sorry, you already have voted from this computer.</h4><br>
    	<p>Click <A HREF="/python/cgi-bin/showresults.py"> here</A> to see the survey results.</p>
    </body>
</html>

```

This HTML page seems valid.  So I think I am good there.

In my Python script, I have cgitb enabled so that it would show error messages.  But I get no error messages! I also took a look at Tomcat's log files for my webapp, and they are not indicating errors.  But what I noticed is no bytes/data were sent.

I even ran that urllib.urlopen() method locally using a Python editor in my Ubuntu machine, and it showed the HasVoted.html page. I also did the same thing at work and was able to see HasVoted.html.  So I don't know what is wrong!

So...looking back on the problem I had with having to run Tomcat as root user first to get it to run on port 80, I was thinking that perhaps the reason HasVoted.html is not being sent to the client is because it has to do with Ubuntu's strict priviledge rules which are not allowing the urlopen() method to execute??  Is that even possible?  I figure since Linux is very strict so that it is secure, anything is possible.  But the client browser can see other HTML pages that my Ubuntu server is serving, so I don't know how Ubuntu/Linux can make a distinction like that.

I don't know, I am totally stumped!  Any help on this is greatly appreciated.

BTW, I launch the Tomcat server by first executing sudo -s to switch to root user, then I launch Tomcat's startup.sh script.  Don't know if that tid bit of info would help.

---

### Post by danandjan on 2010-04-14
Yes!!  I found the problem or a bug??  But I think it is perhaps a bug in the urlopen() method.  If I change the contents of HasVoted.html file to:
```

Content-type: text/html


<title>Already Voted
</title>
 
<body> 
    <h4>Sorry, you already have voted from this computer.</h4><br> 
    <p>Click <A HREF="/python/cgi-bin/showresults.py"> here</A> to see the survey results.</p> 
</body>

```

it works!

For some reason, the Python CGI module isn't recognising the html header in the original HasVoted.html file when it is opened via urlopen() method. All I did was add the Content-Type line at the top to force it to recognise it as a html file.  But why must I do this??  It works fine on my old winxp machine.  Perhaps the urlopen() method behaves differently on Linux.  Very strange.  This will have to do for now.  Dang that took me on a wild ride!

---

