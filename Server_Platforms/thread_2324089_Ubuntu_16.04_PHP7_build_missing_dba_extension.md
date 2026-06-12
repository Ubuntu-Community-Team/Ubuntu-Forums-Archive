---
title: "Ubuntu 16.04 PHP7 build missing dba extension"
date: 2016-05-10
forum: Server Platforms
---

### Post by Michael_Shaffer on 2016-05-10
Hello,

I'm attempting to set up a Ubuntu server running 16.04. 
One of the system services is a php cli program that uses the [dba php extension]("http://php.net/manual/en/dba.installation.php") according to [launchpad.net]("https://launchpad.net/ubuntu/xenial/amd64/php7.0-cli/7.0.3-3") it appears that this is built into the version of php that is released with 16.04 but when running php from the command line it says that the dba_open function doesn't exist.
Does anyone know what I'm missing here?
I'd really prefer not to have to maintain a custom build of PHP on the server if possible.

Also I didn't see any php7.0-{extension} packages in the repositories that contained the dba extension.

Thanks in advanced.

---

### Post by Michael_Shaffer on 2016-05-10
just ran the following with no return.

```

php -i | grep dba

```

```

php -a
var_dump( function_exists('dba_open') );
bool(false)

```

---

### Post by Michael_Shaffer on 2016-05-10
Also noticed that the /etc/php/7.0/cli/php.ini file has
```

[dba]
;dba.default_handler=

```

so it would seem that it's built in but the module functions don't exist in php?

---

### Post by Michael_Shaffer on 2016-05-11
Found that I was looking at an earlier release of the php7.0-cli package on launch pad when I verified that it was included, the latest is [here]("https://launchpad.net/ubuntu/xenial/amd64/php7.0-cli/7.0.4-7ubuntu2").  The latest version doesn't state that it is included.  Posted a [question to launchpad]("https://answers.launchpad.net/ubuntu/+question/293591") about why this change was made.

I'll post back here if I'm able to determine the availability of this extension and the others that were dropped ( bcmath calendar ctype dba dom exif fileinfo ftp gettext iconv mbstring mysqlnd PDO Phar posix shmop SimpleXML soap sockets standard sysvmsg sysvsem sysvshm tokenizer xml xmlreader xmlwriter ) from the default build.

---

