---
title: "ubuntu upgrade"
date: 2007-07-11
forum: Repositories &amp; Backports
---

### Post by pete992000 on 2007-07-11
Hi all

I cannot use the upgrade as I am getting an installation error. A broken package. I ran apt-get with the -f option and got this. Anyone help please?

quote
(Reading database ... 170740 files and directories currently installed.)
Preparing to replace python-uno 2.0.4-0ubuntu5 (using .../python-uno_2.0.4-0ubuntu6_i386.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in <module>
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 935, in run
    pkg.remove(runtimes, remove_script_files=True)
  File "/usr/bin/pycentral", line 693, in remove
    default_runtime.remove_byte_code(self.private_files)
AttributeError: 'NoneType' object has no attribute 'remove_byte_code'
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in <module>
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 935, in run
    pkg.remove(runtimes, remove_script_files=True)
  File "/usr/bin/pycentral", line 693, in remove
    default_runtime.remove_byte_code(self.private_files)
AttributeError: 'NoneType' object has no attribute 'remove_byte_code'
dpkg: error processing /var/cache/apt/archives/python-uno_2.0.4-0ubuntu6_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python-uno_2.0.4-0ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
unquote

This is blocking any further updates.
 
Thank Pete

---

### Post by dumbbeatnix on 2007-07-11
I too am getting this error on an update it has something to do with python-uno.  Has the repository changed?

This is a list of the errors that I get from the update install program:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_2.2.0-1ubuntu4_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_2.2.0-1ubuntu4_i386.deb)
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_2.2.0-1ubuntu4_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_2.2.0-1ubuntu4_all.deb)
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org_2.2.0-1ubuntu4_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org_2.2.0-1ubuntu4_i386.deb)
  404 Not Found


So it appears as though there are problems with python-uno, ttf-opensymbol and openoffice itself.

Do I need to upgrade my OS from fiesty to something else?  Or is there a problem with your servers?

P.S. I will also post a forum topic on this.

Cheers
dumbbeatnix

---

### Post by pete992000 on 2007-07-11
Sorry in my original post I forget to mention that I am using Edgy

Regards Pete

---

