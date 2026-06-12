---
title: "Trac/SVN httpd.conf Configuration questions"
date: 2011-06-10
forum: Server Platforms
---

### Post by Fugan on 2011-06-10
Hi,

I am working to configure a trac/svn server and I have a question about the configuration file.  Here is a sample of the file I am using for a single project (there are multiple):

```

        WSGIScriptAlias /Test_1 /srv/trac/Test_1/deploy/cgi-bin/trac.wsgi
        <Directory /srv/trac/Test_1/deploy/cgi-bin>
                AuthType Basic
                AuthName "Trac"
                Require group staff test_1

                WSGIApplicationGroup %{GLOBAL}
                Order deny,allow
                Allow from all
        </Directory>

        <location /Test_1/svn>
                DAV svn
                SVNPath /srv/svn/Test_1
        </Location>

```On the trac site, they usually add a new location like so:
```

<location /Test_1/login >
                AuthType Basic
                AuthName "Trac"
                Require group staff test_1
</location>

```to handle users, and have no authentication stuff in the Directory/WSGI Alias section.  My question is, does this setup have a bad security flaw that I am overlooking? I am not an apache dev at all, so some of this is a little more black magic than I wish.  I would love to have the time to learn exactly what is happening here, but until then I need to know if this is ok.

The reason why I am setting things up like this is we have a single server that hosts ALL the trac/svn projects.  The server uses basic_auth + ssl for security.  The root of the server (/) allows all users from the staff group, with AllowOveride set to AuthConfig.  This means I can create new projects for individual groups like above (group test_1).  I tried configuring this behaviour using the login location, but I had no luck, so I removed that location and tied the authorization to the entire project directory.  Is this bad? 

If you have a suggestion for a better idea, I don't need my hand held, but a gently nudge in the right direction would be helpful.  My Google foo has failed me (too many common search terms) and I keep circling the same example, which uses the /login location and doesn't seem to work.

If I'm not creating a major security hole, I will leave it as is.  I understand HOW the /login location works, I just don't understand WHY it is necessary, if that makes sense.

To anyone who read this post, thanks for sticking with it!:KS
Thanks!

---

