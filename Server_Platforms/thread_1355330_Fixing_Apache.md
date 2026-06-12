---
title: "Fixing Apache"
date: 2009-12-14
forum: Server Platforms
---

### Post by Vegan on 2009-12-14
My httpd.conf file

```

<IfModule mod_userdir.c>
    UserDir www
</IfModule>

<Directory /home/*/www>
    AllowOverride FileInfo AuthConfig Limit
    Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
    <Limit GET POST OPTION>
        Order allow,deny
	Allow from all
    </Limit>
    <LimitExcept GET POST OPTION>
	Order deny,allow
	Deny from all
    </LimitExcept>
</Directory>

```

So I am using a simple 2 liner for the sites, one for the directory and the other for the domain.

Ideas why I cant get no satisfaction?

---

### Post by HighCommander540 on 2009-12-14
> **Vegan said:**
> My httpd.conf file

```

<IfModule mod_userdir.c>
    UserDir www
</IfModule>

<Directory /home/*/www>
    AllowOverride FileInfo AuthConfig Limit
    Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
    <Limit GET POST OPTION>
        Order allow,deny
	Allow from all
    </Limit>
    <LimitExcept GET POST OPTION>
	Order deny,allow
	Deny from all
    </LimitExcept>
</Directory>

```

So I am using a simple 2 liner for the sites, one for the directory and the other for the domain.

Ideas why I cant get no satisfaction?

Yes, this happens all the time for people trying to use Ubuntu. First, off. Get rid of all of it. You need to put this stuff in "/etc/apache2/sites-available/default" otherwise Apache will load both and nothing will happen.

Plus, all of that looks. Like it interferes with itself. You have a Limit GET POST. Then you have a Limitexcept GET POST.

---

### Post by Vegan on 2009-12-14
Should I drop the limit and limitexcept sections completely. I just put it in httpd.conf as I was not wanting to muck with the default files.

Anything I should add or is this all I really need. I do not need CGI as I am using PHP.

---

### Post by HighCommander540 on 2009-12-14
> **Vegan said:**
> Should I drop the limit and limitexcept sections completely. I just put it in httpd.conf as I was not wanting to muck with the default files.

Anything I should add or is this all I really need. I do not need CGI as I am using PHP.

Yeah, you can just get rid of the CGI stuff. I do. Not that PHP isn't CGI. Read what CGI actually means ;).

I would just get rid of them, I have never needed them. Besides why wouldn't you allow your server to use cookies and sessions?

You should always use one or the other. If you really want to use the httpd.conf then you need to empty the default file. Otherwise they screw with each other.

---

### Post by Vegan on 2009-12-14
I use phpBB and it uses cookies for logins etc. That is standard fare for any web development and can be done with JavaScript easily.

Anyway I nuked the crud and I noticed that vhosts are still not being recognized even with a link to in the available area.

---

### Post by toddedw on 2009-12-15
Personally I haven't touched httpd.conf since apache2. I like the power of using /etc/apache2/sites-available coupled with sites-enabled.

My current setup is as follows: I defined a virtualhost for each of my IPs and setup my personal sites in default. Then I have a single config file for each of my users. This gives me the power to enable/disable my users hosting without having to edit a config file. My httpd.conf simply defines my ServerName so that I don't get that silly error when apache starts.

---

### Post by Vegan on 2009-12-15
I put general stuff in the httpd.conf as specifics in the sites-available. I then use a symbolic link to sites-enabled.

---

