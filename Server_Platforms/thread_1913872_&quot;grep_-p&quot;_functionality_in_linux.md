---
title: "&quot;grep -p&quot; functionality in linux"
date: 2012-01-23
forum: Server Platforms
---

### Post by MakOwner on 2012-01-23
I don't know if this is the right spot for this - if a moderator knows of a better forum, would you please move it?

I learned to write korn shell scripts in AIX and the grep command there has the -p "paragraph" function/parameter.  I'm sure most everyone is familiar with this, it's incredibly useful when parsing log files in scripts.

gnu grep doesn't have this functionality, although it's been requested a number of times -- requests for this functionality usually meet a response like this: [http://savannah.gnu.org/bugs/?14630#discussion](http://savannah.gnu.org/bugs/?14630#discussion) 

Which are great if you are doing it as a one off command line thing, but try doing that with variables in a script and for me at least they fail miserably.  


Are there ways to reproduce this behavior in linux that I'm just dumb enough not to know about?
Anyone interested in banding together and recreating the feature?

---

### Post by mario.niessner on 2012-01-23
Paragrep works for me...

[http://software.clapper.org/paragrep/](http://software.clapper.org/paragrep/)

Hope it will for you.

---

### Post by MakOwner on 2012-06-22
> **mario.niessner said:**
> Paragrep works for me...

[http://software.clapper.org/paragrep/](http://software.clapper.org/paragrep/)

Hope it will for you.

I can't get it installed.

The version called by the pip and easy_install program is version 3.1.0
That version doesn't exist at the URL where the installer is directed.
There doesn't appear to be anyway to direct the installer to use an earlier or local version of the package.

Any ideas?

---

### Post by rubylaser on 2012-06-22
Why don't you just grab the source from the git repo?
```
apt-get install git
```
```
git clone git://github.com/bmc/paragrep.git
```
```
cd paragrep
```
```
python setup.py install
```

---

### Post by MakOwner on 2012-06-22
> **rubylaser said:**
> Why don't you just grab the source from the git repo?
```
apt-get install git
```
```
git clone git://github.com/bmc/paragrep.git
```
```
cd paragrep
```
```
python setup.py install
```

Working on that now.

---

### Post by MakOwner on 2012-06-22
> **MakOwner said:**
> Working on that now.

```

Downloading http://pypi.python.org/packages/any/g/grizzled-python/grizzled-python-1.0.3.linux-x86_64.tar.gz#md5=dcd4e2506db7320d215eefcd2b16c17f
Processing grizzled-python-1.0.3.linux-x86_64.tar.gz
error: Couldn't find a setup script in /tmp/easy_install-epn7M4/grizzled-python-1.0.3.linux-x86_64.tar.gz

```

On to other things for the day. 

This is on Centos 6.2, by the way, so no easy apt repository to use.

---

### Post by hawkmage on 2012-06-22
> **MakOwner said:**
> This is on Centos 6.2, by the way, so no easy apt repository to use.
OK, I have to ask.  Why are you posting this to a Ubuntu Server forum if you are running CentOS?

Since I deal with both flavors of Linux you may want to try the following to install get:
```
sudo yum install get
```

---

### Post by rubylaser on 2012-06-22
> **hawkmage said:**
> OK, I have to ask.  Why are you posting this to a Ubuntu Server forum if you are running CentOS?

Since I deal with both flavors of Linux you may want to try the following to install get:
```
sudo yum install get
```

I assume you mean this :)
```
sudo yum install git
```

---

### Post by rubylaser on 2012-06-22
> **MakOwner said:**
> ```

Downloading http://pypi.python.org/packages/any/g/grizzled-python/grizzled-python-1.0.3.linux-x86_64.tar.gz#md5=dcd4e2506db7320d215eefcd2b16c17f
Processing grizzled-python-1.0.3.linux-x86_64.tar.gz
error: Couldn't find a setup script in /tmp/easy_install-epn7M4/grizzled-python-1.0.3.linux-x86_64.tar.gz

```

On to other things for the day. 

This is on Centos 6.2, by the way, so no easy apt repository to use.

That install script isn't working properly (I see similar errors with easy_install and the git repo). The work around for me was to install grizzled by itself, then remove the dependency from the setup.py file.

```
easy_install grizzled
```

Then, remove this line from your setup.py file.
```
install_requires = ['grizzled-python>=1.0', ],
```

Now, you should be able to get this working from the paragrep git download by running this again.
```
python setup.py install
```

I have it working now.
```
root@test:~# paragrep 
paragrep: error: Not enough arguments.
Not enough arguments.
Usage: 
paragrep [-aiov] [-p EOP_REGEXP] [-e REGEXP] ... [-f EXP_FILE] ... [file] ...
               -OR-
paragrep [-iv] [-p EOP_REGEXP] regexp [file] ...

Options:
  --version             show program's version number and exit
  -h, --help            Show this message and exit.
  -a, --and             Logically AND all regular expressions.
  -e regexp, --regexp=regexp, --expr=regexp
                        Specify a regular expression to find.This option may
                        be specified multiple times.
  -f exprfile, --file=exprfile
                        Specify a file full of regular expressions, one per
                        line.
  -i, --caseblind       Match without regard to case.
  -o, --or              Logically OR all regular expressions.
  -p eop_regexp, --eop=eop_regexp
                        Specify an alternate regular expression to match end-
                        of-paragraph. Default: ^\s*$
  -P, --print-eop       Print the line that marks the end of each paragraph.
                        Default: False
  -v, --negate          Negate the sense of the match.
```

Hope that helps.

---

### Post by David Andersson on 2012-06-23
Other alternatives are awk and perl

```
awk -v RS="" -v ORS="\n\n" '/PATTERN/' [FILENAMES]
```

```
perl -000 -ne 'print if /PATTERN/' [FILENAMES]
```

(Differs from grep in that "/" in pattern must be escaped.)

---

### Post by MakOwner on 2012-06-25
> **hawkmage said:**
> OK, I have to ask.  Why are you posting this to a Ubuntu Server forum if you are running CentOS?

Since I deal with both flavors of Linux you may want to try the following to install get:
```
sudo yum install get
```



Because I'm a glutton for punishment as my mother used to say.
I'm working on some 'proof of concept' functions for a product that is only officially supported with RHEL and SUSE.  CentOS 6.2 is the closest thing to RedHat I can find for testing these scripts.

In reality it makes no difference, but when talking to an entrenched beuracracy (did I spell that right?) at a large TLA company it's easier if you don't have easy targets for potshots.

The fact that I'm cooking this up and not a real programmer should be scary enough.

---

### Post by MakOwner on 2012-06-25
And also thanks to everyone for the alternatives.

---

