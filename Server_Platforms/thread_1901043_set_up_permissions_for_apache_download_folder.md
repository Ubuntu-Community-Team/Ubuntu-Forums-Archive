---
title: "set up permissions for apache download folder"
date: 2011-12-27
forum: Server Platforms
---

### Post by nethero on 2011-12-27
Hi there,

I've just started using apache and I've made a few cgi scripts that generate text files and pictures for users to download.  The thing is that even though I know how to generate these files, I don't know which directory to put them in.  For developement purposes I've been writing them to my desktop but now that the development phase is over I need to create a directory that these files can be placed in; something like /var/www/downloadFilesFromHere.  Obviously I can make this directory by typing  sudo mkdir /var/www/downloadFilesFromHere but how do I set up permissions for this folder so that apache can write to it and users can see it?  Thanks.

---

### Post by SeijiSensei on 2011-12-27
If they really are scripts that execute applications, you need to read [this]("http://httpd.apache.org/docs/current/howto/cgi.html").

---

### Post by nethero on 2011-12-28
> **SeijiSensei said:**
> If they really are scripts that execute applications, you need to read [this]("http://httpd.apache.org/docs/current/howto/cgi.html").

Yes, I'm much further ahead of that.  My apache server is configured to run CGI and I know how to run a CGI script etc. etc.   The thing is that this new CGI script I've written actually produces a file that the user can then download.  I've never had to deal with this before because all of my prior CGI scripts simply printed out some HTML for the browser to display.  I was wondering how to make a download folder and set the permissions so the user could download from it easily.

---

### Post by SeijiSensei on 2011-12-28
Rather than dumping the file into a folder, why not simply send it to the browser directly?  You can force the browser to bring up the "Save As" dialog box using the HTTP "[Content-Disposition]("http://www.ietf.org/rfc/rfc2183.txt")" header.

Otherwise you can write the file to a folder to which the "www-data" user has permissions, then provide the user with a link to the file.  Create a folder like "/var/www/downloads" with 0700 permissions and owned by user "www-data".  That will enable Apache to write the file into the directory and also enable it to read the file to send it to the user with an "http://example.com/downloads/myfile.ext" URL.

---

### Post by rubylaser on 2011-12-28
Both of those are very good suggestions.  Personally, I would use the second method, as it's super easy to script, and is easy to provide a link for the user to download the file.

---

### Post by nethero on 2011-12-28
> **SeijiSensei said:**
> Rather than dumping the file into a folder, why not simply send it to the browser directly?  You can force the browser to bring up the "Save As" dialog box using the HTTP "[Content-Disposition]("http://www.ietf.org/rfc/rfc2183.txt")" header.

Otherwise you can write the file to a folder to which the "www-data" user has permissions, then provide the user with a link to the file.  Create a folder like "/var/www/downloads" with 0700 permissions and owned by user "www-data".  That will enable Apache to write the file into the directory and also enable it to read the file to send it to the user with an "http://example.com/downloads/myfile.ext" URL.

Perfect!  Thanks. Like rubylaser said; I like your second example the best, especially since I may have to reuse these files later.

---

### Post by Vegan on 2011-12-28
chmod 644 seems to be a safe enough configuration

---

### Post by SeijiSensei on 2011-12-29
> **Vegan said:**
> chmod 644 seems to be a safe enough configuration

Since we're talking about a directory, the permissions would be 755.

However I suggested limiting the directory's permissions to 0700 because I don't know how private these files might be.  Suppose, for instance, that the script creates a unique file that should only be readable by the script's user.  You'd want to keep that private from other users on the server.

---

### Post by nethero on 2011-12-29
> **SeijiSensei said:**
> Since we're talking about a directory, the permissions would be 755.

However I suggested limiting the directory's permissions to 0700 because I don't know how private these files might be.  Suppose, for instance, that the script creates a unique file that should only be readable by the script's user.  You'd want to keep that private from other users on the server.

Still new to permissions.  What is the difference between 0700 and 700?  Is there one?  Also I did try 644 but then my CGI script could not write to the directory.  700 worked fine.

---

### Post by SeijiSensei on 2011-12-29
There's a fourth permission bit that applies only in limited circumstances (setuid, setgid, and the "sticky" bit).  It's determined by the first octet in the four-digit scheme.  Read [this]("http://en.wikipedia.org/wiki/Chmod#Symbolic_examples") for more details.

In most ordinary circumstances you can omit the leading zero; e.g., "chmod 755" makes a directory readable and listable for everyone and writable by the directory's owner.

In general directories need to have the execute bit enabled as well as the read and write bits.  If you list the root directory of your system (ls -lr /), you'll see the directories are all owned by root with 755 (or "u+rwx,go+rx") permissions.

---

