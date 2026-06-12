---
title: "vmbuilder - how to specify multiple apt repositories?"
date: 2010-08-03
forum: Virtualisation
---

### Post by cougie on 2010-08-03
Hi there,

I am running the following command on lucid:

 sudo vmbuilder kvm ubuntu  --addpkg apache2  --addpkg an_internal_package --hostname foo

The key point is that an_internal_package resides in a local repository, [http://apt/ourcompany](http://apt/ourcompany).

In this case, vmbuilder complains that it cannot find an_internal_package. How do I tell it that, in addition to looking in [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) for apache, it should look in a local repository for a different package?

Also - a note - the host apt is configured such that 'sudo aptitude search an_internal_package' returns a result, as expected. It would sure be nice if the cmd line simply used the host apt environment.

Thanks!

---

### Post by samosamo on 2010-08-03
Not sure if it has this feature.  Would you consider deploying an apt-proxy server?  Seems like a win/win for you.  Centralize everything into one server, and make it faster at the same time!

---

### Post by cougie on 2010-08-03
Yes, I was actually trying this route, as well. I installed the proxy and added the following block to the 'backends' section of apt-proxy.conf:

[ourcompany]
;;company archive
backends =
        [http://apt/ourcompany]("http://apt/some_component_name")

Then restarted apt-proxy.

I reran the vmbuilder cmd with the additional '--mirror' argument. It still can't find secondary-mono-runtime, the internal package. 

Thanks for your help!

*****************************

sudo vmbuilder kvm ubuntu  --addpkg apache2  --addpkg secondary-mono-runtime --hostname foo --mirror [http://hostip:9999/ubuntu](http://hostip:9999/ubuntu)

2010-08-03 14:58:47,586 INFO    : Calling hook: preflight_check
2010-08-03 14:58:47,590 INFO    : Calling hook: set_defaults
2010-08-03 14:58:47,590 INFO    : Calling hook: bootstrap
2010-08-03 15:06:31,296 INFO    : Calling hook: configure_os
2010-08-03 15:06:37,727 INFO    : E: Couldn't find package secondary-mono-runtime
2010-08-03 15:06:37,728 ERROR   : Process (['chroot', '/var/tmp/tmpv4a4Fq', 'apt-get', 'install', '-y', '--force-yes', 'secondary-mono-runtime', 'vim']) returned 100. stdout: Reading package lists...
Building dependency tree...
, stderr: E: Couldn't find package secondary-mono-runtime

Traceback (most recent call last):
  File "/usr/bin/vmbuilder", line 24, in <module>
    cli.main()
  File "/usr/lib/python2.6/dist-packages/VMBuilder/contrib/cli.py", line 109, in main
    distro.build_chroot()
  File "/usr/lib/python2.6/dist-packages/VMBuilder/distro.py", line 83, in build_chroot
    self.call_hooks('configure_os')
  File "/usr/lib/python2.6/dist-packages/VMBuilder/distro.py", line 66, in call_hooks
    call_hooks(self, *args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/VMBuilder/util.py", line 165, in call_hooks
    getattr(context, func, log_no_such_method)(*args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/VMBuilder/plugins/ubuntu/distro.py", line 151, in configure_os
    self.suite.install_extras()
  File "/usr/lib/python2.6/dist-packages/VMBuilder/plugins/ubuntu/dapper.py", line 202, in install_extras
    self.run_in_target(env={ 'DEBIAN_FRONTEND' : 'noninteractive' }, *cmd)
  File "/usr/lib/python2.6/dist-packages/VMBuilder/plugins/ubuntu/dapper.py", line 327, in run_in_target
    return self.context.run_in_target(*args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/VMBuilder/plugins/__init__.py", line 86, in run_in_target
    return util.run_cmd('chroot', self.chroot_dir, *args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/VMBuilder/util.py", line 120, in run_cmd
    raise VMBuilderException, "Process (%s) returned %d. stdout: %s, stderr: %s" % (args.__repr__(), status, mystdout.buf, mystderr.buf)
VMBuilder.exception.VMBuilderException: Process (['chroot', '/var/tmp/tmpv4a4Fq', 'apt-get', 'install', '-y', '--force-yes', 'secondary-mono-runtime', 'vim']) returned 100. stdout: Reading package lists...
Building dependency tree...
, stderr: E: Couldn't find package secondary-mono-runtime

---

### Post by samosamo on 2010-08-03
oh I see, it still requires the different repository in the URL.  well, I assume you tried two --mirror switches which did not work, in which case I suggest submitting a feature request :)

also you may want to consider utilizing --execscript.  you can add the line in apt.conf and install your pkg like so:

```
chroot $1 echo "deb http://asdf:9999/monoruntime lucid main" >> /etc/apt/sources.list
chroot $1 apt-get update
chroot $1 apt-get upgrade
chroot $1 apt-get install secondary-mono-runtime
```

---

### Post by cougie on 2010-08-12
Hey, that worked. Thanks a lot! The only thing I had to do differently was the following, due to permissions on /etc/apt:

chroot $1 bash -c 'echo "deb [http://apt/foo](http://apt/foo) main" >> /etc/apt/sources.list'

---

### Post by samosamo on 2010-08-13
Nice =D

---

