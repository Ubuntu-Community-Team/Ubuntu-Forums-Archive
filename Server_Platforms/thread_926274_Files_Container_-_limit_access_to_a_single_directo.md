---
title: "Files Container - limit access to a single directory"
date: 2008-09-21
forum: Server Platforms
---

### Post by skunkbad on 2008-09-21
I'm trying to limit access to a file called lastModified.php, which is in my www directory, and I want to limit access to only scripts that are in a single sub directory. When I try this, I get a 500 error. I know the documentation doesn't specify that this can be done, so I need to know the real way to do what I'm trying to do. Here is what I was trying in the .htaccess file:

<Files "lastModified.php">
order deny,allow
deny from all
allow from mysite.com/directory      ##This is the line that is producing the 500 error
</Files>

---

