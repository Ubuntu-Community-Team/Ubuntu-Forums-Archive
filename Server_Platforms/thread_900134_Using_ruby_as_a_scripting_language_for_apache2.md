---
title: "Using ruby as a scripting language for apache2"
date: 2008-08-25
forum: Server Platforms
---

### Post by maxbaroi on 2008-08-25
I installed apache2 and mysql as per the instructions here: [http://wiki.debian.org/LaMp]("http://wiki.debian.org/LaMp").

That is I entered the following:
```
 # aptitude update && aptitude upgrade
 # aptitude install mysql-server mysql-client libmysqlclient15-dev
 # /usr/bin/mysqladmin -u root password 'enter-your-good-new-password-here' 
 # aptitude install apache2 apache2-doc
```

Then I bracnhed off from the isntructions and did
```

# aptitude install ruby
# aptitude install libapache2-mod-ruby

```

To test things out I wrote a simple html file called test.htlm that contained

```
<html>
<body>
This text is <% a = 100; puts "#{a}% Live!" %>

</body>
</html>
```

When I check the page out at 12.7.0.0.1/apache2-default/test.html I see the page, but instead of "This test is 100% Live!" I see 
"This text is <% a = 100; puts "#{a}% Live!" %>"

Any help would be appreciated.

---

### Post by shifty2 on 2008-08-25
I'm pretty certain that <? ?> can only used for having php code inline. If you want to use ruby I would reccomend looking into ruby on rails, or something similar.

---

### Post by Meabed on 2008-08-25
try to rename the file .ruby

---

### Post by maxbaroi on 2008-08-25
There should be a way to do it without using rails since you can use php, python and perl with as scripting languages without a framework. All that's required is libapache2-mod-(php|perl|python), and there's an analgous module for ruby. 

I believe there's a tag like <scripting-language="[your language]", but I haven't been able to find it. 

Changing to .ruby didn't work, probably because the tags aren't correct, but I wouldn't be embedding ruby code into html if I did that.

---

### Post by maxbaroi on 2008-08-25
If I do the same exact process, but with php instead of ruby, everything works fine. So what is going on that ruby doesn't work? Are the tags wrong? Is there something in apache2.conf that I need to change? THis is getting frustrating

---

