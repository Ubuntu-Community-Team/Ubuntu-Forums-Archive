---
title: "Apache2 Server CGI Issue"
date: 2008-07-07
forum: Server Platforms
---

### Post by Yuki_Nagato on 2008-07-07
The situation:

It is all internal right now.  Using one computer to call the pages from the server in my network.  Mod_Python is installed.  The script is python, in a cgi-bin.  The httpd.conf file is configured so that

```
ScriptAlias /cgi-bin/ /home/www/cgi-bin/
```

The log states that I get an Error Number 13 - Permission Denied when the interpreter looks for the Python file to execute it.

Then it tosses an error afterwards stating that there is a "Premature end of script headers," from the same Python file.

The python file called is:

```
#!/usr/bin/python

import cgi

def main():
	print "Content-type: text/html\n"
	print "Hello World"
	
main()
```

Simply, I am trying to test out the Python setup with as simple a file as possible.

Is it a file owner issue?

---

### Post by windependence on 2008-07-08
You may have to make the script executable. It could also be an issue with the permissions or ownership of the CGI script.

-Tim

---

### Post by Yuki_Nagato on 2008-07-08
Right-clicked on the file and allowed it to be executable.  Folder access and stuff I am not worrying about because it is not underneath the "DocumentRoot."  But changing the executable status worked.


Now I have another question.  Everytime I upload this file, I have to change the ability to execute it.  Where can I go to have this set before hand?  I heard somewhere that child files take on the status of their parents directories, but I am unclear about this.

Thank You.

---

### Post by windependence on 2008-07-08
Hmmmm.....I don't think you can set the whole directory to "executable". the problem is the file is probably taking on the permissions of the user that created it. I'm thinking you may have to make it executable each time unfortunately.

-Tim

---

