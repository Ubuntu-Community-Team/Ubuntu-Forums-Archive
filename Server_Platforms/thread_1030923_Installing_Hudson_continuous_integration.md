---
title: "Installing Hudson continuous integration"
date: 2009-01-04
forum: Server Platforms
---

### Post by tinny on 2009-01-04
Hello

Im wanting to install [Hudson]("https://hudson.dev.java.net/") my my 8.04 server. 

I tried following these instructions and unfortunately I had no luck.

[http://weblogs.java.net/blog/kohsuke/archive/2008/06/debian_packages.html](http://weblogs.java.net/blog/kohsuke/archive/2008/06/debian_packages.html)

Id like to install Hudson from an apt repository, any ideas?

Thanks :-)

---

### Post by tinny on 2009-01-06
I ended up installing Hudson from one of the deb packages that can be found in the repository linked to above.

This deb package installs Hudson as a daemon. Once installed it runs fine, but if I restart the server it fails to start this daemon. If I try and run it manually I get the following.

```

$ sudo /etc/init.d/hudson start
[sudo] password for hermes: 
Invalid --pidfile argument: '/var/run/hudson/hudson.pid' (Parent directory does not exist)
usage: daemon [options] [cmd arg...]
options:

      -h, --help              - Print a help message then exit
      -V, --version           - Print a version message then exit
      -v, --verbose[=level]   - Set the verbosity level
      -d, --debug[=level]     - Set the debugging level

      -C, --config=path       - Specify the configuration file
      -N, --noconfig          - Bypass the system configuration file
      -n, --name=name         - Guarantee a single named instance
      -X, --command=cmd       - Specify the client command as an option
      -P, --pidfiles=/dir     - Override standard pidfile location
      -F, --pidfile=/path     - Override standard pidfile name and location

      -u, --user=user[.group] - Run the client as user[.group]
      -R, --chroot=path       - Run the client with path as root
      -D, --chdir=path        - Run the client in directory path
      -m, --umask=umask       - Run the client with the given umask
      -e, --env="var=val"     - Set a client environment variable
      -i, --inherit           - Inherit environment variables
      -U, --unsafe            - Allow execution of unsafe executable
      -S, --safe              - Deny execution of unsafe executable
      -c, --core              - Allow core file generation

      -r, --respawn           - Respawn the client when it terminates
      -a, --acceptable=#      - Minimum acceptable client duration
      -A, --attempts=#        - Respawn # times on error before delay
      -L, --delay=#           - Delay between spawn attempt bursts (seconds)
      -M, --limit=#           - Maximum number of spawn attempt bursts

      -f, --foreground        - Run the client in the foreground
      -p, --pty[=noecho]      - Allocate a pseudo terminal for the client

      -l, --errlog=spec       - Send daemon's error output to syslog or file
      -b, --dbglog=spec       - Send daemon's debug output to syslog or file
      -o, --output=spec       - Send client's output to syslog or file
      -O, --stdout=spec       - Send client's stdout to syslog or file
      -E, --stderr=spec       - Send client's stderr to syslog or file

          --running           - Check if a named daemon is running
          --restart           - Restart a named daemon client
          --stop              - Terminate a named daemon process
Invalid --pidfile argument: '/var/run/hudson/hudson.pid' (Parent directory does not exist)
usage: daemon [options] [cmd arg...]
options:

      -h, --help              - Print a help message then exit
      -V, --version           - Print a version message then exit
      -v, --verbose[=level]   - Set the verbosity level
      -d, --debug[=level]     - Set the debugging level

      -C, --config=path       - Specify the configuration file
      -N, --noconfig          - Bypass the system configuration file
      -n, --name=name         - Guarantee a single named instance
      -X, --command=cmd       - Specify the client command as an option
      -P, --pidfiles=/dir     - Override standard pidfile location
      -F, --pidfile=/path     - Override standard pidfile name and location

      -u, --user=user[.group] - Run the client as user[.group]
      -R, --chroot=path       - Run the client with path as root
      -D, --chdir=path        - Run the client in directory path
      -m, --umask=umask       - Run the client with the given umask
      -e, --env="var=val"     - Set a client environment variable
      -i, --inherit           - Inherit environment variables
      -U, --unsafe            - Allow execution of unsafe executable
      -S, --safe              - Deny execution of unsafe executable
      -c, --core              - Allow core file generation

      -r, --respawn           - Respawn the client when it terminates
      -a, --acceptable=#      - Minimum acceptable client duration
      -A, --attempts=#        - Respawn # times on error before delay
      -L, --delay=#           - Delay between spawn attempt bursts (seconds)
      -M, --limit=#           - Maximum number of spawn attempt bursts

      -f, --foreground        - Run the client in the foreground
      -p, --pty[=noecho]      - Allocate a pseudo terminal for the client

      -l, --errlog=spec       - Send daemon's error output to syslog or file
      -b, --dbglog=spec       - Send daemon's debug output to syslog or file
      -o, --output=spec       - Send client's output to syslog or file
      -O, --stdout=spec       - Send client's stdout to syslog or file
      -E, --stderr=spec       - Send client's stderr to syslog or file

          --running           - Check if a named daemon is running
          --restart           - Restart a named daemon client
          --stop              - Terminate a named daemon process


```

If I manually create the /var/run/hudson/ folder and make hudson the owner I can then successfully start hudson.

So this looks like a daemon setup problem, what can I do to fix this problem? (obviously its not ideal to have to do this manual process after each restart)

Thanks.

---

### Post by phecht on 2009-10-04
Hello,

I used the instructions located here: [http://weblogs.java.net/blog/kohsuke/archive/2008/06/debian_packages.html](http://weblogs.java.net/blog/kohsuke/archive/2008/06/debian_packages.html) as you have.  I had no issues.  I wish I could help more.

After installing via apt, it starts automatically.  I don't have to do sudo anything after the apt-get.  I think you are getting the error message because hudson is already started.  Therefore 8080 is already in use?  

I am using Ubuntu 9.04.  

Sincerely,

Pete

---

