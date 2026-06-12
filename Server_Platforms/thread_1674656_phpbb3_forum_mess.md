---
title: "phpbb3 forum mess"
date: 2011-01-24
forum: Server Platforms
---

### Post by objet petit a on 2011-01-24
Hello everybody,

I am trying to set up a phpbb3 forum, running on mysql with apache. However, I am an absolute noob at a lot of things. So, the situation is as follows:

- I installed the [LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP") stack sort of correctly.
- I have an existing database, which I should import
- I have not created a database in sql yet.
- When I open my localhost in my browser I am seeing the page being served, but no content.

In the [tutorial](https://help.ubuntu.com/community/PhpBB3) it showed a phpbb3 login screen as an example of what it should do when I was successful. I am not seeing it. Is this due to the lack of a database in mysql? And if this is the case, should I import a database directly, or create a database first and then import the file into the database?

NOTE:
There may be some details not properly dealt with from the LAMP stack. I gave it a rest after deciding that I might not have to create a database, but rather import one. This may be an important clue to whomever is an expert at this, so I figured I'd mention this.

---

### Post by wongo888 on 2011-01-24
PHP is famous for serving up blank pages. The best thing to do in these cases is to check your Apache log files, in this case the error log. It will tell you what is going wrong.

Make good use of the phpinfo function and check your permissions too.

---

### Post by objet petit a on 2011-01-25
The apache log files are empty. What does that mean?

---

### Post by wongo888 on 2011-01-25
Are you able to view a phpinfo page?

[http://php.net/manual/en/function.phpinfo.php](http://php.net/manual/en/function.phpinfo.php)

If your loglevel is set to Warn in Apache, and your logging is set up properly in php then php errors should be sent to the Apache error log. If you are getting a white page then errors should be showing up in the error log.

---

