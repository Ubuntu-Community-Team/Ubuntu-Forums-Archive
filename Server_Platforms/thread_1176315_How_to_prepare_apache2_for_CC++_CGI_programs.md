---
title: "How to prepare apache2 for C/C++ CGI programs?"
date: 2009-06-02
forum: Server Platforms
---

### Post by resander on 2009-06-02
I have some large applications written in C/C++ that I would like to access from the web, so this is case for CGI as far as I know. I would put the executables in the cgi_bin directory and add code that converts the output from these to html to be sent to the browser. They access MySQL database via ODBC.

I have just installed appache2 on Ubuntu 8.10, but I have never used it before. The apache2 documentation is very detailed and difficult to interpret for a beginner like myself. I have googled on cgi and found that most server programming is in PHP or PERL. I don't know these and would want to do all server programming in C/C++.

I would like to use apache2 default settings as much as possible, but how do I config apache2 to let me use Linux executables instead of PHP/PERL?

---

