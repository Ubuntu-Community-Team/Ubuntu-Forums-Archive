---
title: "technique to query server files from client and allow download of outputted results"
date: 2012-06-17
forum: Ubuntu Dev Link Forum
---

### Post by cdaringe on 2012-06-17
good evening again, all.  I have a design Q.  i have a bunch of files stored in a nice hierarchy on my server.  I have a text box, where when the user enters a string, & I want the user to be able to click a button and show all the files in a directory that is tied to that string (by tied to, i simply mean  on the server the files may be stored like /directory/<string in textbox>/files).  i need  a function to read that textbox value on the client side, call the server directory, query it's contents, and return links to those files in the directory to the page.  then, hopefully, allow the user to download the returned files.  any points in a good direction?

thanks!

-Chris

---

### Post by mevun on 2012-07-21
Do you mean client like a web browser?  Because the typical thing is to have an webpage with a form in it to send the "text".  Then the web server provides another web page this time with the names of the files found on the server.  This page can have the other button(s) to download files.  Like each filename shown could be a link that starts a download.

So with a soln like this, you don't need any special client software (because presumably everyone has a web browser).  All you have to do is come up with the web server software.  Here there are lots of choices obviously which can use a variety of programming languages.

Sorry if this is too vague, but your question seemed pretty general and I'm not really sure if I provided any info that you didn't already know.  I say that because a web server solution is pretty much standard nowadays.

---

