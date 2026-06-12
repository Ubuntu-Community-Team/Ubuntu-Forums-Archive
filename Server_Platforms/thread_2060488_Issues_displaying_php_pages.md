---
title: "Issues displaying php pages"
date: 2012-09-20
forum: Server Platforms
---

### Post by Fatesauce on 2012-09-20
Hi everyone, long time reader first time poster!

I have been setting up a web server on an old box, remotely, following these instructions:
[http://funwithlinux.net/2012/05/ubuntu-12-04-web-server/](http://funwithlinux.net/2012/05/ubuntu-12-04-web-server/)
Everything up to testing php has worked so far.  But when I got to view index.php through my workstations browser, it just appears blank.  I installed php5, even removed and reinstalled it.  I dont have experience setting up php on a server so I am not sure how to fix this.

Any help would be awesome, thanks!

---

### Post by spjackson on 2012-09-20
A frequent cause of a blank page from php is a syntax error or similar in the php script you are trying to run. Is an error reported in /var/log/apache2/error.log?

---

### Post by Fatesauce on 2012-09-20
Awesome, that was it.

```
echo \'hello\';
```

That line was returning an error.

---

