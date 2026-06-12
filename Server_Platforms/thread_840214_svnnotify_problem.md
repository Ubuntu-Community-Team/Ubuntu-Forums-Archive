---
title: "svnnotify problem"
date: 2008-06-25
forum: Server Platforms
---

### Post by janskey on 2008-06-25
Hi

I'm having problem with my svn notify colordiff: here the details

# vi post-commit

#!/bin/sh
REPOS="$1"
REV="$2"
svnnotify --repos-path "$1" --revision "$2" --to [email]myemail@example.org[/email] --from [email]anotheremail@example.org[/email] --handler HTML:ColorDiff -d

# ls -al post-commit <--post-commit is located in hooks of svn repo
-rwxr-xr-x 1 www-data www-data 2011 Jun 25 10:50 post-commit

# perl -MCPAN -e 'install SVN::Notify'
CPAN: File::HomeDir loaded ok (v0.69)
CPAN: Storable loaded ok (v2.15)
Going to read /root/.cpan/Metadata
  Database was generated on Wed, 25 Jun 2008 06:02:49 GMT
CPAN: YAML loaded ok (v0.66)
Going to read /root/.cpan/build/
DONE
Found no old builds, restored the state of none
SVN::Notify is up to date (2.75).

# perl -MCPAN -e 'install SVN::Notify::HTML::ColorDiff'
CPAN: File::HomeDir loaded ok (v0.69)
CPAN: Storable loaded ok (v2.15)
Going to read /root/.cpan/Metadata
  Database was generated on Wed, 25 Jun 2008 06:02:49 GMT
CPAN: YAML loaded ok (v0.66)
Going to read /root/.cpan/build/
DONE
Found no old builds, restored the state of none
SVN::Notify::HTML::ColorDiff is up to date (2.75).

# which svnnotify
/usr/local/bin/svnnotify

testing svnnotify:

# ./post-commit /opt/svn/repo/maproject 2
syntax error at (eval 1) line 1, near "require SVN::Notify::HTML:"

Any hints?

---

### Post by netstv on 2009-06-11
> **janskey said:**
> Hi

I'm having problem with my svn notify colordiff: here the details

# vi post-commit

#!/bin/sh
REPOS="$1"
REV="$2"
svnnotify --repos-path "$1" --revision "$2" --to [email]myemail@example.org[/email] --from [email]anotheremail@example.org[/email] --handler HTML:ColorDiff -d

# ls -al post-commit <--post-commit is located in hooks of svn repo
-rwxr-xr-x 1 www-data www-data 2011 Jun 25 10:50 post-commit

# perl -MCPAN -e 'install SVN::Notify'
CPAN: File::HomeDir loaded ok (v0.69)
CPAN: Storable loaded ok (v2.15)
Going to read /root/.cpan/Metadata
  Database was generated on Wed, 25 Jun 2008 06:02:49 GMT
CPAN: YAML loaded ok (v0.66)
Going to read /root/.cpan/build/
DONE
Found no old builds, restored the state of none
SVN::Notify is up to date (2.75).

# perl -MCPAN -e 'install SVN::Notify::HTML::ColorDiff'
CPAN: File::HomeDir loaded ok (v0.69)
CPAN: Storable loaded ok (v2.15)
Going to read /root/.cpan/Metadata
  Database was generated on Wed, 25 Jun 2008 06:02:49 GMT
CPAN: YAML loaded ok (v0.66)
Going to read /root/.cpan/build/
DONE
Found no old builds, restored the state of none
SVN::Notify::HTML::ColorDiff is up to date (2.75).

# which svnnotify
/usr/local/bin/svnnotify

testing svnnotify:

# ./post-commit /opt/svn/repo/maproject 2
syntax error at (eval 1) line 1, near "require SVN::Notify::HTML:"

Any hints?

I just had this same problem..... I figured it out.  Not a very good error message (well at least to me).

The problem is the line "--handler HTML:ColorDiff"

You need to have two colons between HTML and ColorDiff.

HTML::ColorDiff

Hope that helps.

-stv

---

