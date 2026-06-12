---
title: "How to TOR without X ?"
date: 2010-08-31
forum: Security
---

### Post by pehden on 2010-08-31
Any one know how to make tor run without the gui i would like to run it on a seperate machine that doesnt have GUI but it doesnt want to start with out a X

---

### Post by bodhi.zazen on 2010-08-31
> **pehden said:**
> Any one know how to make tor run without the gui i would like to run it on a seperate machine that doesnt have GUI but it doesnt want to start with out a X

This is an old thread and your question is unrelated to the OP question, you should start a new thread, so I am moving this post for you.

What gave you the idea that TOR uses X in any way ? 

You install TOR + a proxy (privoxy or polipo, your choice). X is not required at all.

If you are installing into a central server you will need to configure your proxy and iptables as well, the exact details are dependent on how you wish to configure your clients and if you want the proxy to be transparent.

For TOR see :

[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

[http://www.torproject.org/docs/debian.html.en](http://www.torproject.org/docs/debian.html.en)

[http://blog.bodhizazen.net/linux/how-to-transparent-proxy/](http://blog.bodhizazen.net/linux/how-to-transparent-proxy/)

You will need to adapt ;)

---

### Post by pehden on 2010-09-01
Cause when i was trying to start it it said failed to start X, i finally got it started and running and even set up apache2 to proxy the port as a webdomain name but it never loads, any one got this set up like this with out a gui.

---

### Post by bodhi.zazen on 2010-09-01
I run TOR with Privoxy without a gui all the time.

What does Apache have to do with running TOR ?

What guide are you following and what have you done. What is the exact error message you are getting when you try to run what application ?

I already gave you two links on how to set up TOR :

[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

[http://www.torproject.org/docs/debian.html.en](http://www.torproject.org/docs/debian.html.en)

Did you read them ? What part do you not understand ?

---

### Post by pehden on 2010-09-01
Ok using those sources im still haveing issues getting it to work.

I have it set up on the server and my apache is set to proxy the port from 9050 to a virtual domain aka pro.domain.ltd  i go to the site directly and it says tor is a socks proxy but when i make FF connect to the domain on port 80 it fails the pages time out or load then nothing happens. Any Ideas.

---

### Post by bodhi.zazen on 2010-09-01
> **pehden said:**
> Ok using those sources im still haveing issues getting it to work.

I have it set up on the server and my apache is set to proxy the port from 9050 to a virtual domain aka pro.domain.ltd  i go to the site directly and it says tor is a socks proxy but when i make FF connect to the domain on port 80 it fails the pages time out or load then nothing happens. Any Ideas.

What does apache have to do with TOR ?

---

### Post by pehden on 2010-09-01
I have apache set up to proxy the listening port for tor, so when i go some where i dont have to run tor on every one elses network, and i could just proxy to home server and let it run my tor from there, as well when i go some places like my work they got only port 80 and 443 open.


> **bodhi.zazen said:**
> What does apache have to do with TOR ?

---

### Post by bodhi.zazen on 2010-09-01
I am not sure how you would do that exactly, proxy TOR with apache. Typically you would run TOR on your client, with what you describe, I suggest TOR portable, runs on USB with Linux and Windows.

Honestly I do not think TOR is exactly what you want, I would suggest ssh :

[Proxy Firefox through a SSH tunnel "how to" @ Calomel.org - Open Source Research and Reference]("https://calomel.org/firefox_ssh_proxy.html") 

If needed, you can configure privoxy to serve as a proxy, but again I have no idea why you are using apache.

If you need assistance, you need to provide more information. Simply stating that it does not work does not give us much to go on. Again, what how to are you using, what makes you think you should be using apache, and we also need more detailed information on your exact configuration. Please do not post the entire config file, just the sections you modified.

---

### Post by pehden on 2010-09-01
Im running tor on my web server I am also running apache im setting up a virtual host that when i connect to it as in going to proxy setting in FF and setting my vhost domain it would connect to my webserver, ok my major reason is it is easier to explain to some one what to put in for the proxy settings then to tell get them to download something and install then it.

Im setting this up so other people can use my server as a proxy it will be open but then its still private because the main hostname is not what will be doing this it will be a sub domain. I explained so far that I got this all set up but im not sure why tor isnt letting the users connect.

here are my .conf

```

#    Sample Configuration File for Privoxy
#
#  Id: config,v
#
#  Copyright (C) 2001-2009 Privoxy Developers http://www.privoxy.org/
#
####################################################################
#                                                                  #
#                      Table of Contents                           #
#                                                                  #
#        I. INTRODUCTION                                           #
#       II. FORMAT OF THE CONFIGURATION FILE                       #
#                                                                  #
#        1. LOCAL SET-UP DOCUMENTATION                             #
#        2. CONFIGURATION AND LOG FILE LOCATIONS                   #
#        3. DEBUGGING                                              #
#        4. ACCESS CONTROL AND SECURITY                            #
#        5. FORWARDING                                             #
#        6. WINDOWS GUI OPTIONS                                    #
#                                                                  #
####################################################################
#
#
#  I. INTRODUCTION
#   ===============
#
#  This file holds Privoxy's main configuration. Privoxy detects
#  configuration changes automatically, so you don't have to restart
#  it unless you want to load a different configuration file.
#
#  The configuration will be reloaded with the first request after
#  the change was done, this request itself will still use the old
#  configuration, though. In other words: it takes two requests before
#  you see the result of your changes.  Requests that are dropped due
#  to ACL don't trigger reloads.
#
#  When starting Privoxy on Unix systems, give the location of this
#  file as last argument. On Windows systems, Privoxy will look for
#  this file with the name 'config.txt' in the current working directory
#  of the Privoxy process.
#
#
#  II. FORMAT OF THE CONFIGURATION FILE
#  ====================================
#
#  Configuration lines consist of an initial keyword followed by a
#  list of values, all separated by whitespace (any number of spaces
#  or tabs). For example,
#
#  actionsfile default.action
#
#  Indicates that the actionsfile is named 'default.action'.
#
#  The '#' indicates a comment. Any part of a line following a '#'
#  is ignored, except if the '#' is preceded by a '\'.
#
#  Thus, by placing a # at the start of an existing configuration
#  line, you can make it a comment and it will be treated as if it
#  weren't there. This is called "commenting out" an option and can
#  be useful. Removing the # again is called "uncommenting".
#
#  Note that commenting out an option and leaving it at its default
#  are two completely different things! Most options behave very
#  differently when unset.  See the "Effect if unset" explanation in
#  each option's description for details.
#
#  Long lines can be continued on the next line by using a `\' as the
#  last character.
#
#
#
#  1. LOCAL SET-UP DOCUMENTATION
#  ==============================
#
#  If you intend to operate Privoxy for more users than just yourself,
#  it might be a good idea to let them know how to reach you, what
#  you block and why you do that, your policies, etc.
#
#
#
#  1.1. user-manual
#  =================
#
#  Specifies:
#
#      Location of the Privoxy User Manual.
#
#  Type of value:
#
#      A fully qualified URI
#
#  Default value:
#
#      Unset
#
#  Effect if unset:
#
#      http://www.privoxy.org/version/user-manual/ will be used,
#      where version is the Privoxy version.
#
#  Notes:
#
#      The User Manual URI is the single best source of information on
#      Privoxy, and is used for help links from some of the internal
#      CGI pages. The manual itself is normally packaged with the
#      binary distributions, so you probably want to set this to a
#      locally installed copy.
#
#      Examples:
#
#      The best all purpose solution is simply to put the full local
#      PATH to where the User Manual is located:
#
#        user-manual  /usr/share/doc/privoxy/user-manual
#
#
#      The User Manual is then available to anyone with
#      access to Privoxy, by following the built-in URL:
#      http://config.privoxy.org/user-manual/ (or the shortcut:
#      http://p.p/user-manual/).
#
#      If the documentation is not on the local system, it can be
#      accessed from a remote server, as:
#
#        user-manual  http://example.com/privoxy/user-manual/
#
#
#      WARNING!!!
#
#          If set, this option should be the first option in the config
#          file, because it is used while the config file is being read.
#
user-manual /usr/share/doc/privoxy/user-manual
#
#
#  1.2. trust-info-url
#  ====================
#
#  Specifies:
#
#      A URL to be displayed in the error page that users will see if
#      access to an untrusted page is denied.
#
#  Type of value:
#
#      URL
#
#  Default value:
#
#      Unset
#
#  Effect if unset:
#
#      No links are displayed on the "untrusted" error page.
#
#  Notes:
#
#      The value of this option only matters if the experimental trust
#      mechanism has been activated. (See trustfile below.)
#
#      If you use the trust mechanism, it is a good idea to write
#      up some on-line documentation about your trust policy and to
#      specify the URL(s) here. Use multiple times for multiple URLs.
#
#      The URL(s) should be added to the trustfile as well, so users
#      don't end up locked out from the information on why they were
#      locked out in the first place!
#
#trust-info-url  http://www.example.com/why_we_block.html
#trust-info-url  http://www.example.com/what_we_allow.html
#
#
#  1.3. admin-address
#  ===================
#
#  Specifies:
#
#      An email address to reach the Privoxy administrator.
#
#  Type of value:
#
#      Email address
#
#  Default value:
#
#      Unset
#
#  Effect if unset:
#
#      No email address is displayed on error pages and the CGI user
#      interface.
#
#  Notes:
#
#      If both admin-address and proxy-info-url are unset, the whole
#      "Local Privoxy Support" box on all generated pages will not
#      be shown.
#
admin-address ****
#
#  1.4. proxy-info-url
#  ====================
#
#  Specifies:
#
#      A URL to documentation about the local Privoxy setup,
#      configuration or policies.
#
#  Type of value:
#
#      URL
#
#  Default value:
#
#      Unset
#
#  Effect if unset:
#
#      No link to local documentation is displayed on error pages and
#      the CGI user interface.
#
#  Notes:
#
#      If both admin-address and proxy-info-url are unset, the whole
#      "Local Privoxy Support" box on all generated pages will not
#      be shown.
#
#      This URL shouldn't be blocked ;-)
#
proxy-info-url *
#
#
#  2. CONFIGURATION AND LOG FILE LOCATIONS
#  ========================================
#
#  Privoxy can (and normally does) use a number of other files for
#  additional configuration, help and logging. This section of the
#  configuration file tells Privoxy where to find those other files.
#
#  The user running Privoxy, must have read permission for all
#  configuration files, and write permission to any files that would
#  be modified, such as log files and actions files.
#
#
#
#  2.1. confdir
#  =============
#
#  Specifies:
#
#      The directory where the other configuration files are located.
#
#  Type of value:
#
#      Path name
#
#  Default value:
#
#      /etc/privoxy (Unix) or Privoxy installation dir (Windows)
#
#  Effect if unset:
#
#      Mandatory
#
#  Notes:
#
#      No trailing "/", please.
#
confdir /etc/privoxy
#
#
#  2.2. templdir
#  ==============
#
#  Specifies:
#
#      An alternative directory where the templates are loaded from.
#
#  Type of value:
#
#      Path name
#
#  Default value:
#
#      unset
#
#  Effect if unset:
#
#      The templates are assumed to be located in confdir/template.
#
#  Notes:
#
#      Privoxy's original templates are usually overwritten with each
#      update. Use this option to relocate customized templates that
#      should be kept. As template variables might change between
#      updates, you shouldn't expect templates to work with Privoxy
#      releases other than the one they were part of, though.
#
#templdir .
#
#
#  2.3. logdir
#  ============
#
#  Specifies:
#
#      The directory where all logging takes place (i.e. where the
#      logfile is located).
#
#  Type of value:
#
#      Path name
#
#  Default value:
#
#      /var/log/privoxy (Unix) or Privoxy installation dir (Windows)
#
#  Effect if unset:
#
#      Mandatory
#
#  Notes:
#
#      No trailing "/", please.
#
logdir /var/log/privoxy
#
#
#  2.4. actionsfile
#  =================
#
#  Specifies:
#
#      The actions file(s) to use
#
#  Type of value:
#
#      Complete file name, relative to confdir
#
#  Default values:
#
#        match-all.action # Actions that are applied to all sites and maybe overruled later on.
#
#        default.action   # Main actions file
#
#        user.action      # User customizations
#
#  Effect if unset:
#
#      No actions are taken at all. More or less neutral proxying.
#
#  Notes:
#
#      Multiple actionsfile lines are permitted, and are in fact
#      recommended!
#
#      The default values are default.action, which is the "main"
#      actions file maintained by the developers, and user.action,
#      where you can make your personal additions.
#
#      Actions files contain all the per site and per URL configuration
#      for ad blocking, cookie management, privacy considerations,
#      etc. There is no point in using Privoxy without at least one
#      actions file.
#
#      Note that since Privoxy 3.0.7, the complete filename, including
#      the ".action" extension has to be specified. The syntax change
#      was necessary to be consistent with the other file options and
#      to allow previously forbidden characters.
#
actionsfile match-all.action # Actions that are applied to all sites and maybe overruled later on.
actionsfile default.action   # Main actions file
actionsfile user.action      # User customizations
#
#
#  2.5. filterfile
#  ================
#
#  Specifies:
#
#      The filter file(s) to use
#
#  Type of value:
#
#      File name, relative to confdir
#
#  Default value:
#
#      default.filter (Unix) or default.filter.txt (Windows)
#
#  Effect if unset:
#
#      No textual content filtering takes place, i.e. all +filter{name}
#      actions in the actions files are turned neutral.
#
#  Notes:
#
#      Multiple filterfile lines are permitted.
#
#      The filter files contain content modification rules that use
#      regular expressions. These rules permit powerful changes on the
#      content of Web pages, and optionally the headers as well, e.g.,
#      you could try to disable your favorite JavaScript annoyances,
#      re-write the actual displayed text, or just have some fun
#      playing buzzword bingo with web pages.
#
#      The +filter{name} actions rely on the relevant filter (name)
#      to be defined in a filter file!
#
#      A pre-defined filter file called default.filter that contains a
#      number of useful filters for common problems is included in the
#      distribution. See the section on the filter action for a list.
#
#      It is recommended to place any locally adapted filters into a
#      separate file, such as user.filter.
#
filterfile default.filter
#filterfile user.filter      # User customizations
#
#
#  2.6. logfile
#  =============
#
#  Specifies:
#
#      The log file to use
#
#  Type of value:
#
#      File name, relative to logdir
#
#  Default value:
#
#      Unset (commented out). When activated: logfile (Unix) or
#      privoxy.log (Windows).
#
#  Effect if unset:
#
#      No logfile is written.
#
#  Notes:
#
#      The logfile is where all logging and error messages are
#      written. The level of detail and number of messages are set with
#      the debug option (see below).  The logfile can be useful for
#      tracking down a problem with Privoxy (e.g., it's not blocking
#      an ad you think it should block) and it can help you to monitor
#      what your browser is doing.
#
#      Depending on the debug options below, the logfile may be a
#      privacy risk if third parties can get access to it. As most
#      users will never look at it, Privoxy 3.0.7 and later only log
#      fatal errors by default.
#
#      For most troubleshooting purposes, you will have to change that,
#      please refer to the debugging section for details.
#
#      Your logfile will grow indefinitely, and you will probably
#      want to periodically remove it. On Unix systems, you can do
#      this with a cron job (see "man cron"). For Red Hat based Linux
#      distributions, a logrotate script has been included.
#
#      Any log files must be writable by whatever user Privoxy is
#      being run as (on Unix, default user id is "privoxy").
#
logfile logfile
#
#
#  2.7. trustfile
#  ===============
#
#  Specifies:
#
#      The name of the trust file to use
#
#  Type of value:
#
#      File name, relative to confdir
#
#  Default value:
#
#      Unset (commented out). When activated: trust (Unix) or trust.txt
#      (Windows)
#
#  Effect if unset:
#
#      The entire trust mechanism is disabled.
#
#  Notes:
#
#      The trust mechanism is an experimental feature for building
#      white-lists and should be used with care. It is NOT recommended
#      for the casual user.
#
#      If you specify a trust file, Privoxy will only allow access to
#      sites that are specified in the trustfile. Sites can be listed
#      in one of two ways:
#
#      Prepending a ~ character limits access to this site only (and
#      any sub-paths within this site), e.g. ~www.example.com allows
#      access to ~www.example.com/ features/news.html, etc.
#
#      Or, you can designate sites as trusted referrers, by prepending
#      the name with a + character. The effect is that access to
#      untrusted sites will be granted -- but only if a link from
#      this trusted referrer was used to get there. The link target
#      will then be added to the "trustfile" so that future, direct
#      accesses will be granted. Sites added via this mechanism do
#      not become trusted referrers themselves (i.e. they are added
#      with a ~ designation). There is a limit of 512 such entries,
#      after which new entries will not be made.
#
#      If you use the + operator in the trust file, it may grow
#      considerably over time.
#
#      It is recommended that Privoxy be compiled with the
#      --disable-force, --disable-toggle and --disable-editor options,
#      if this feature is to be used.
#
#      Possible applications include limiting Internet access for
#      children.
#
#trustfile trust
#
#
#  3. DEBUGGING
#  =============
#
#  These options are mainly useful when tracing a problem. Note that
#  you might also want to invoke Privoxy with the --no-daemon command
#  line option when debugging.
#
#
#
#  3.1. debug
#  ===========
#
#  Specifies:
#
#      Key values that determine what information gets logged.
#
#  Type of value:
#
#      Integer values
#
#  Default value:
#
#      0 (i.e.: only fatal errors (that cause Privoxy to exit) are logged)
#
#  Effect if unset:
#
#      Default value is used (see above).
#
#  Notes:
#
#      The available debug levels are:
#
#        debug         1 # Log the destination for each request Privoxy let through. See also debug 1024.
#        debug         2 # show each connection status
#        debug         4 # show I/O status
#        debug         8 # show header parsing
#        debug        16 # log all data written to the network into the logfile
#        debug        32 # debug force feature
#        debug        64 # debug regular expression filters
#        debug       128 # debug redirects
#        debug       256 # debug GIF de-animation
#        debug       512 # Common Log Format
#        debug      1024 # Log the destination for requests Privoxy didn't let through, and the reason why.
#        debug      2048 # CGI user interface
#        debug      4096 # Startup banner and warnings.
#        debug      8192 # Non-fatal errors
#
#
#      To select multiple debug levels, you can either add them or
#      use multiple debug lines.
#
#      A debug level of 1 is informative because it will show you each
#      request as it happens. 1, 1024, 4096 and 8192 are recommended
#      so that you will notice when things go wrong. The other levels
#      are probably only of interest if you are hunting down a specific
#      problem. They can produce a hell of an output (especially 16).
#
#      Privoxy used to ship with the debug levels recommended above
#      enabled by default, but due to privacy concerns 3.0.7 and later
#      are configured to only log fatal errors.
#
#      If you are used to the more verbose settings, simply enable
#      the debug lines below again.
#
#      If you want to use pure CLF (Common Log Format), you should set
#      "debug 512" ONLY and not enable anything else.
#
#      Privoxy has a hard-coded limit for the length of log messages. If
#      it's reached, messages are logged truncated and marked with
#      "... [too long, truncated]".
#
#      Please don't file any support requests without trying to
#      reproduce the problem with increased debug level first. Once
#      you read the log messages, you may even be able to solve the
#      problem on your own.
#
debug      1 # Log the destination for each request Privoxy let through.
debug   1024 # Log the destination for requests Privoxy didn't let through, and the reason why.
debug   4096 # Startup banner and warnings
debug   8192 # Non-fatal errors
#
#
#  3.2. single-threaded
#  =====================
#
#  Specifies:
#
#      Whether to run only one server thread.
#
#  Type of value:
#
#      None
#
#  Default value:
#
#      Unset
#
#  Effect if unset:
#
#      Multi-threaded (or, where unavailable: forked) operation,
#      i.e. the ability to serve multiple requests simultaneously.
#
#  Notes:
#
#      This option is only there for debugging purposes. It will
#      drastically reduce performance.
#
#single-threaded
#
#
#  3.3. hostname
#  ==============
#
#  Specifies:
#
#      The hostname shown on the CGI pages.
#
#  Type of value:
#
#      Text
#
#  Default value:
#
#      Unset
#
#  Effect if unset:
#
#      The hostname provided by the operating system is used.
#
#  Notes:
#
#      On some misconfigured systems resolving the hostname fails or
#      takes too much time and slows Privoxy down. Setting a fixed
#      hostname works around the problem.
#
#      In other circumstances it might be desirable to show a hostname
#      other than the one returned by the operating system. For example
#      if the system has several different hostnames and you don't
#      want to use the first one.
#
#      Note that Privoxy does not validate the specified hostname value.
#
hostname *
#
#
#  4. ACCESS CONTROL AND SECURITY
#  ===============================
#
#  This section of the config file controls the security-relevant
#  aspects of Privoxy's configuration.
#
#
#
#  4.1. listen-address
#  ====================
#
#  Specifies:
#
#      The IP address and TCP port on which Privoxy will listen for
#      client requests.
#
#  Type of value:
#
#      [IP-Address]:Port
#
#  Default value:
#
#      127.0.0.1:8118
#
#  Effect if unset:
#
#      Bind to 127.0.0.1 (IPv4 localhost), port 8118. This is suitable
#      and recommended for home users who run Privoxy on the same
#      machine as their browser.
#
#  Notes:
#
#      You will need to configure your browser(s) to this proxy address
#      and port.
#
#      If you already have another service running on port 8118, or
#      if you want to serve requests from other machines (e.g. on your
#      local network) as well, you will need to override the default.
#
#      IPv6 addresses containing colons have to be quoted by brackets.
#
#      If you leave out the IP address, Privoxy will bind to all IPv4
#      interfaces (addresses) on your machine and may become reachable
#      from the Internet. In that case, consider using access control
#      lists (ACL's, see below), and/or a firewall. If the hostname
#      is localhost, Privoxy will explicitly try to bind to an IPv4
#      address. For other hostnames it depends on the operating system
#      which IP version will be used.
#
#      If you open Privoxy to untrusted users, you will also
#      want to make sure that the following actions are disabled:
#      enable-edit-actions and enable-remote-toggle
#
#  Example:
#
#      Suppose you are running Privoxy on a machine which has the
#      address 192.168.0.1 on your local private network (192.168.0.0)
#      and has another outside connection with a different address. You
#      want it to serve requests from inside only:
#
#        listen-address  192.168.0.1:8118
#
#
#      Suppose you are running Privoxy on an IPv6-capable machine and
#      you want it to listen on the IPv6 address of the loopback device:
#
#        listen-address [::1]:8118
#
#
listen-address  0.0.0.0:8118
#
#
#  4.2. toggle
#  ============
#
#  Specifies:
#
#      Initial state of "toggle" status
#
#  Type of value:
#
#      1 or 0
#
#  Default value:
#
#      1
#
#  Effect if unset:
#
#      Act as if toggled on
#
#  Notes:
#
#      If set to 0, Privoxy will start in "toggled off" mode,
#      i.e. mostly behave like a normal, content-neutral proxy
#      with both ad blocking and content filtering disabled. See
#      enable-remote-toggle below.
#
#      The windows version will only display the toggle icon in the
#      system tray if this option is present.
#
toggle  1
#
#
#  4.3. enable-remote-toggle
#  ==========================
#
#  Specifies:
#
#      Whether or not the web-based toggle feature may be used
#
#  Type of value:
#
#      0 or 1
#
#  Default value:
#
#      0
#
#  Effect if unset:
#
#      The web-based toggle feature is disabled.
#
#  Notes:
#
#      When toggled off, Privoxy mostly acts like a normal,
#      content-neutral proxy, i.e. doesn't block ads or filter content.
#
#      Access to the toggle feature can not be controlled separately by
#      "ACLs" or HTTP authentication, so that everybody who can access
#      Privoxy (see "ACLs" and listen-address above) can toggle it
#      for all users. So this option is not recommended for multi-user
#      environments with untrusted users.
#
#      Note that malicious client side code (e.g Java) is also capable
#      of using this option.
#
#      As a lot of Privoxy users don't read documentation, this feature
#      is disabled by default.
#
#      Note that you must have compiled Privoxy with support for this
#      feature, otherwise this option has no effect.
#
enable-remote-toggle  0
#
#
#  4.4. enable-remote-http-toggle
#  ===============================
#
#  Specifies:
#
#      Whether or not Privoxy recognizes special HTTP headers to change
#      its behaviour.
#
#  Type of value:
#
#      0 or 1
#
#  Default value:
#
#      0
#
#  Effect if unset:
#
#      Privoxy ignores special HTTP headers.
#
#  Notes:
#
#      When toggled on, the client can change Privoxy's behaviour by
#      setting special HTTP headers. Currently the only supported
#      special header is "X-Filter: No", to disable filtering for
#      the ongoing request, even if it is enabled in one of the
#      action files.
#
#      This feature is disabled by default. If you are using Privoxy in
#      a environment with trusted clients, you may enable this feature
#      at your discretion. Note that malicious client side code (e.g
#      Java) is also capable of using this feature.
#
#      This option will be removed in future releases as it has been
#      obsoleted by the more general header taggers.
#
enable-remote-http-toggle  0
#
#
#  4.5. enable-edit-actions
#  =========================
#
#  Specifies:
#
#      Whether or not the web-based actions file editor may be used
#
#  Type of value:
#
#      0 or 1
#
#  Default value:
#
#      0
#
#  Effect if unset:
#
#      The web-based actions file editor is disabled.
#
#  Notes:
#
#      Access to the editor can not be controlled separately by
#      "ACLs" or HTTP authentication, so that everybody who can access
#      Privoxy (see "ACLs" and listen-address above) can modify its
#      configuration for all users.
#
#      This option is not recommended for environments with untrusted
#      users and as a lot of Privoxy users don't read documentation,
#      this feature is disabled by default.
#
#      Note that malicious client side code (e.g Java) is also capable
#      of using the actions editor and you shouldn't enable this
#      options unless you understand the consequences and are sure
#      your browser is configured correctly.
#
#      Note that you must have compiled Privoxy with support for this
#      feature, otherwise this option has no effect.
#
enable-edit-actions 0
#
#
#  4.6. enforce-blocks
#  ====================
#
#  Specifies:
#
#      Whether the user is allowed to ignore blocks and can "go there
#      anyway".
#
#  Type of value:
#
#      0 or 1
#
#  Default value:
#
#      0
#
#  Effect if unset:
#
#      Blocks are not enforced.
#
#  Notes:
#
#      Privoxy is mainly used to block and filter requests as a service
#      to the user, for example to block ads and other junk that clogs
#      the pipes.  Privoxy's configuration isn't perfect and sometimes
#      innocent pages are blocked. In this situation it makes sense to
#      allow the user to enforce the request and have Privoxy ignore
#      the block.
#
#      In the default configuration Privoxy's "Blocked" page contains
#      a "go there anyway" link to adds a special string (the force
#      prefix) to the request URL. If that link is used, Privoxy
#      will detect the force prefix, remove it again and let the
#      request pass.
#
#      Of course Privoxy can also be used to enforce a network
#      policy. In that case the user obviously should not be able to
#      bypass any blocks, and that's what the "enforce-blocks" option
#      is for. If it's enabled, Privoxy hides the "go there anyway"
#      link. If the user adds the force prefix by hand, it will not
#      be accepted and the circumvention attempt is logged.
#
#  Examples:
#
#      enforce-blocks 1
#
enforce-blocks 0
#
#
#  4.7. ACLs: permit-access and deny-access
#  =========================================
#
#  Specifies:
#
#      Who can access what.
#
#  Type of value:
#
#      src_addr[:port][/src_masklen] [dst_addr[:port][/dst_masklen]]
#
#      Where src_addr and dst_addr are IPv4 addresses in dotted
#      decimal notation or valid DNS names, port is a port number, and
#      src_masklen and dst_masklen are subnet masks in CIDR notation,
#      i.e. integer values from 2 to 30 representing the length
#      (in bits) of the network address. The masks and the whole
#      destination part are optional.
#
#      If your system implements RFC 3493, then src_addr and dst_addr
#      can be IPv6 addresses delimeted by brackets, port can be a
#      number or a service name, and src_masklen and dst_masklen can
#      be a number from 0 to 128.
#
#  Default value:
#
#      Unset
#
#      If no port is specified, any port will match. If no src_masklen
#      or src_masklen is given, the complete IP address has to match
#      (i.e. 32 bits for IPv4 and 128 bits for IPv6).
#
#  Effect if unset:
#
#      Don't restrict access further than implied by listen-address
#
#  Notes:
#
#      Access controls are included at the request of ISPs and systems
#      administrators, and are not usually needed by individual
#      users. For a typical home user, it will normally suffice to
#      ensure that Privoxy only listens on the localhost (127.0.0.1)
#      or internal (home) network address by means of the listen-address
#      option.
#
#      Please see the warnings in the FAQ that Privoxy is not intended
#      to be a substitute for a firewall or to encourage anyone to
#      defer addressing basic security weaknesses.
#
#      Multiple ACL lines are OK. If any ACLs are specified, Privoxy
#      only talks to IP addresses that match at least one permit-access
#      line and don't match any subsequent deny-access line. In other
#      words, the last match wins, with the default being deny-access.
#
#      If Privoxy is using a forwarder (see forward below) for a
#      particular destination URL, the dst_addr that is examined is
#      the address of the forwarder and NOT the address of the ultimate
#      target. This is necessary because it may be impossible for the
#      local Privoxy to determine the IP address of the ultimate target
#      (that's often what gateways are used for).
#
#      You should prefer using IP addresses over DNS names, because
#      the address lookups take time. All DNS names must resolve! You
#      can not use domain patterns like "*.org" or partial domain
#      names. If a DNS name resolves to multiple IP addresses, only
#      the first one is used.
#
#      Some systems allows IPv4 client to connect to IPv6 server
#      socket. Then the client's IPv4 address will be translated by
#      system into IPv6 address space with special prefix ::ffff:0:0/96
#      (so called IPv4 mapped IPv6 address).  Privoxy can handle it
#      and maps such ACL addresses automatically.
#
#      Denying access to particular sites by ACL may have undesired
#      side effects if the site in question is hosted on a machine
#      which also hosts other sites (most sites are).
#
#  Examples:
#
#      Explicitly define the default behavior if no ACL and
#      listen-address are set: "localhost" is OK. The absence of a
#      dst_addr implies that all destination addresses are OK:
#
#        permit-access  localhost
#
#
#      Allow any host on the same class C subnet as www.privoxy.org
#      access to nothing but www.example.com (or other domains hosted
#      on the same system):
#
#        permit-access  www.privoxy.org/24 www.example.com/32
#
#
#      Allow access from any host on the 26-bit subnet 192.168.45.64 to
#      anywhere, with the exception that 192.168.45.73 may not access
#      the IP address behind www.dirty-stuff.example.com:
#
#        permit-access  192.168.45.64/26 
#        deny-access   192.168.45.73  www.dirty-stuff.example.com
#
#      Allow access from the IPv4 network 192.0.2.0/24 even if listening
#      on an IPv6 wild card address (not supported on all platforms):
#
#        permit-access  192.0.2.0/24
#
#
#      This is equivalent to the following line even if listening on
#      an IPv4 address (not supported on all platforms):
#
#        permit-access  [::ffff:192.0.2.0]/120
#
#
#  4.8. buffer-limit
#  ==================
#
#  Specifies:
#
#      Maximum size of the buffer for content filtering.
#
#  Type of value:
#
#      Size in Kbytes
#
#  Default value:
#
#      4096
#
#  Effect if unset:
#
#      Use a 4MB (4096 KB) limit.
#
#  Notes:
#
#      For content filtering, i.e. the +filter and +deanimate-gif
#      actions, it is necessary that Privoxy buffers the entire document
#      body. This can be potentially dangerous, since a server could
#      just keep sending data indefinitely and wait for your RAM to
#      exhaust -- with nasty consequences.  Hence this option.
#
#      When a document buffer size reaches the buffer-limit, it is
#      flushed to the client unfiltered and no further attempt to filter
#      the rest of the document is made. Remember that there may be
#      multiple threads running, which might require up to buffer-limit
#      Kbytes each, unless you have enabled "single-threaded" above.
#
buffer-limit 4096
#
#
#  5. FORWARDING
#  ==============
#
#  This feature allows routing of HTTP requests through a chain of
#  multiple proxies.
#
#  Forwarding can be used to chain Privoxy with a caching proxy to
#  speed up browsing. Using a parent proxy may also be necessary if
#  the machine that Privoxy runs on has no direct Internet access.
#
#  Note that parent proxies can severely decrease your privacy
#  level. For example a parent proxy could add your IP address to the
#  request headers and if it's a caching proxy it may add the "Etag"
#  header to revalidation requests again, even though you configured
#  Privoxy to remove it. It may also ignore Privoxy's header time
#  randomization and use the original values which could be used by
#  the server as cookie replacement to track your steps between visits.
#
#  Also specified here are SOCKS proxies. Privoxy supports the SOCKS
#  4 and SOCKS 4A protocols.
#
#
#
#  5.1. forward
#  =============
#
#  Specifies:
#
#      To which parent HTTP proxy specific requests should be routed.
#
#  Type of value:
#
#      target_pattern http_parent[:port]
#
#      where target_pattern is a URL pattern that specifies to which
#      requests (i.e. URLs) this forward rule shall apply. Use /
#      to denote "all URLs".  http_parent[:port] is the DNS name or
#      IP address of the parent HTTP proxy through which the requests
#      should be forwarded, optionally followed by its listening port
#      (default: 8000). Use a single dot (.) to denote "no forwarding".
#
#  Default value:
#
#      Unset
#
#  Effect if unset:
#
#      Don't use parent HTTP proxies.
#
#  Notes:
#
#      If http_parent is ".", then requests are not forwarded to
#      another HTTP proxy but are made directly to the web servers.
#
#      http_parent can be a numerical IPv6 address (if RFC 3493 is
#      implemented).  To prevent clashes with the port delimiter,
#      the whole IP address has to be put into brackets. On the other
#      hand a target_pattern containing an IPv6 address has to be put
#      into angle brackets (normal brackets are reserved for regular
#      expressions already).
#
#      Multiple lines are OK, they are checked in sequence, and the
#      last match wins.
#
#  Examples:
#
#      Everything goes to an example parent proxy, except SSL on port
#      443 (which it doesn't handle):
#
#        forward   /      parent-proxy.example.org:8080 
#        forward   :443   .
#
#
#      Everything goes to our example ISP's caching proxy, except for
#      requests to that ISP's sites:
#
#        forward   /                  caching-proxy.isp.example.net:8000
#        forward   .isp.example.net   .
#
#
#      Parent proxy specified by an IPv6 address:
#
#        foward   /                   [2001:DB8::1]:8000
#
#
#      Suppose your parent proxy doesn't support IPv6:
#
#        forward  /                        parent-proxy.example.org:8000
#        forward  ipv6-server.example.org  .
#        forward  <[2-3][0-9a-f][0-9a-f][0-9a-f]:*>   .
#
#
#  5.2. forward-socks4, forward-socks4a and forward-socks5
#  ========================================================
#
#  Specifies:
#
#      Through which SOCKS proxy (and optionally to which parent HTTP
#      proxy) specific requests should be routed.
#
#  Type of value:
#
#      target_pattern socks_proxy[:port] http_parent[:port]
#
#      where target_pattern is a URL pattern that specifies to which
#      requests (i.e. URLs) this forward rule shall apply. Use / to
#      denote "all URLs".  http_parent and socks_proxy are IP addresses
#      in dotted decimal notation or valid DNS names (http_parent may
#      be "." to denote "no HTTP forwarding"), and the optional port
#      parameters are TCP ports, i.e. integer values from 1 to 65535
#
#  Default value:
#
#      Unset
#
#  Effect if unset:
#
#      Don't use SOCKS proxies.
#
#  Notes:
#
#      Multiple lines are OK, they are checked in sequence, and the
#      last match wins.
#
#      The difference between forward-socks4 and forward-socks4a
#      is that in the SOCKS 4A protocol, the DNS resolution of the
#      target hostname happens on the SOCKS server, while in SOCKS 4
#      it happens locally.
#
#      With forward-socks5 the DNS resolution will happen on the remote
#      server as well.
#
#      socks_proxy and http_parent can be a numerical IPv6 address
#      (if RFC 3493 is implemented). To prevent clashes with the port
#      delimiter, the whole IP address has to be put into brackets. On
#      the other hand a target_pattern containing an IPv6 address has
#      to be put into angle brackets (normal brackets are reserved
#      for regular expressions already).
#
#      If http_parent is ".", then requests are not forwarded to another
#      HTTP proxy but are made (HTTP-wise) directly to the web servers,
#      albeit through a SOCKS proxy.
#
#  Examples:
#
#      From the company example.com, direct connections are made to all
#      "internal" domains, but everything outbound goes through their
#      ISP's proxy by way of example.com's corporate SOCKS 4A gateway
#      to the Internet.
#
#        forward-socks4a   /       socks-gw.example.com:1080    www-cache.isp.example.net:8080 
#        forward           .example.com        .
#
#
#      A rule that uses a SOCKS 4 gateway for all destinations but no
#      HTTP parent looks like this:
#
        forward-socks4a   / localhost:9050  .
#
#
#      To chain Privoxy and Tor, both running on the same system,
#      you would use something like:
#
#        forward-socks5   /               127.0.0.1:9050 .
#
#
#      The public Tor network can't be used to reach your local network,
#      if you need to access local servers you therefore might want
#      to make some exceptions:
#
#        forward         192.168.*.*/     .  
#        forward         10.*.*.*/        .  
#        forward         127.*.*.*/       .
#
#
#      Unencrypted connections to systems in these address ranges will
#      be as (un) secure as the local network is, but the alternative
#      is that you can't reach the local network through Privoxy at
#      all. Of course this may actually be desired and there is no
#      reason to make these exceptions if you aren't sure you need them.
#
#      If you also want to be able to reach servers in your local
#      network by using their names, you will need additional exceptions
#      that look like this:
#
#       forward           localhost/     .
#
#
#
#
#  5.3. forwarded-connect-retries
#  ===============================
#
#  Specifies:
#
#      How often Privoxy retries if a forwarded connection request
#      fails.
#
#  Type of value:
#
#      Number of retries.
#
#  Default value:
#
#      0
#
#  Effect if unset:
#
#      Connections forwarded through other proxies are treated like
#      direct connections and no retry attempts are made.
#
#  Notes:
#
#      forwarded-connect-retries is mainly interesting for socks4a
#      connections, where Privoxy can't detect why the connections
#      failed. The connection might have failed because of a DNS timeout
#      in which case a retry makes sense, but it might also have failed
#      because the server doesn't exist or isn't reachable. In this
#      case the retry will just delay the appearance of Privoxy's
#      error message.
#
#      Note that in the context of this option, "forwarded connections"
#      includes all connections that Privoxy forwards through other
#      proxies. This option is not limited to the HTTP CONNECT method.
#
#      Only use this option, if you are getting lots of
#      forwarding-related error messages that go away when you try again
#      manually. Start with a small value and check Privoxy's logfile
#      from time to time, to see how many retries are usually needed.
#
#  Examples:
#
#      forwarded-connect-retries 1
#
forwarded-connect-retries  0
#
#
#  6. MISCELLANEOUS
#  =================
#
#  6.1. accept-intercepted-requests
#  =================================
#
#  Specifies:
#
#      Whether intercepted requests should be treated as valid.
#
#  Type of value:
#
#      0 or 1
#
#  Default value:
#
#      0
#
#  Effect if unset:
#
#      Only proxy requests are accepted, intercepted requests are
#      treated as invalid.
#
#  Notes:
#
#      If you don't trust your clients and want to force them to use
#      Privoxy, enable this option and configure your packet filter
#      to redirect outgoing HTTP connections into Privoxy.
#
#      Make sure that Privoxy's own requests aren't redirected as well.
#      Additionally take care that Privoxy can't intentionally connect
#      to itself, otherwise you could run into redirection loops if
#      Privoxy's listening port is reachable by the outside or an
#      attacker has access to the pages you visit.
#
#  Examples:
#
#      accept-intercepted-requests 1
#
accept-intercepted-requests 0
#
#
#  6.2. allow-cgi-request-crunching
#  =================================
#
#  Specifies:
#
#      Whether requests to Privoxy's CGI pages can be blocked or
#      redirected.
#
#  Type of value:
#
#      0 or 1
#
#  Default value:
#
#      0
#
#  Effect if unset:
#
#      Privoxy ignores block and redirect actions for its CGI pages.
#
#  Notes:
#
#      By default Privoxy ignores block or redirect actions for
#      its CGI pages.  Intercepting these requests can be useful in
#      multi-user setups to implement fine-grained access control,
#      but it can also render the complete web interface useless and
#      make debugging problems painful if done without care.
#
#      Don't enable this option unless you're sure that you really
#      need it.
#
#  Examples:
#
#      allow-cgi-request-crunching 1
#
allow-cgi-request-crunching 0
#
#
#  6.3. split-large-forms
#  =======================
#
#  Specifies:
#
#      Whether the CGI interface should stay compatible with broken
#      HTTP clients.
#
#  Type of value:
#
#      0 or 1
#
#  Default value:
#
#      0
#
#  Effect if unset:
#
#      The CGI form generate long GET URLs.
#
#  Notes:
#
#      Privoxy's CGI forms can lead to rather long URLs. This isn't
#      a problem as far as the HTTP standard is concerned, but it can
#      confuse clients with arbitrary URL length limitations.
#
#      Enabling split-large-forms causes Privoxy to divide big forms
#      into smaller ones to keep the URL length down. It makes editing
#      a lot less convenient and you can no longer submit all changes
#      at once, but at least it works around this browser bug.
#
#      If you don't notice any editing problems, there is no reason
#      to enable this option, but if one of the submit buttons appears
#      to be broken, you should give it a try.
#
#  Examples:
#
#      split-large-forms 1
#
split-large-forms 0
#
#
#  6.4. keep-alive-timeout
#  ========================
#
#  Specifies:
#
#      Number of seconds after which an open connection will no longer
#      be reused.
#
#  Type of value:
#
#      Time in seconds.
#
#  Default value:
#
#      None
#
#  Effect if unset:
#
#      Connections are not kept alive.
#
#  Notes:
#
#      This option allows clients to keep the connection to Privoxy
#      alive. If the server supports it, Privoxy will keep the
#      connection to the server alive as well. Under certain
#      circumstances this may result in speed-ups.
#
#      By default, Privoxy will close the connection to the server if
#      the client connection gets closed, or if the specified timeout
#      has been reached without a new request coming in. This behaviour
#      can be changed with the connection-sharing option.
#
#      This option has no effect if Privoxy has been compiled without
#      keep-alive support.
#
#  Examples:
#
#      keep-alive-timeout 300
#
keep-alive-timeout 300
#
#
#  6.5. connection-sharing
#  ========================
#
#  Specifies:
#
#      Whether or not outgoing connections that have been kept alive
#      should be shared between different incoming connections.
#
#  Type of value:
#
#      0 or 1
#
#  Default value:
#
#      None
#
#  Effect if unset:
#
#      Connections are not shared.
#
#  Notes:
#
#      This option has no effect if Privoxy has been compiled without
#      keep-alive support, or if it's disabled.
#
#  Notes:
#
#      Note that reusing connections doesn't necessary cause
#      speedups. There are also a few privacy implications you should
#      be aware of.
#
#      If this option is effective, outgoing connections are shared
#      between clients (if there are more than one) and closing the
#      browser that initiated the outgoing connection does no longer
#      affect the connection between Privoxy and the server unless
#      the client's request hasn't been completed yet.
#
#      If the outgoing connection is idle, it will not be closed until
#      either Privoxy's or the server's timeout is reached. While
#      it's open, the server knows that the system running Privoxy is
#      still there.
#
#      If there are more than one client (maybe even belonging to
#      multiple users), they will be able to reuse each others
#      connections. This is potentially dangerous in case of
#      authentication schemes like NTLM where only the connection
#      is authenticated, instead of requiring authentication for
#      each request.
#
#      If there is only a single client, and if said client can keep
#      connections alive on its own, enabling this option has next to
#      no effect. If the client doesn't support connection keep-alive,
#      enabling this option may make sense as it allows Privoxy to keep
#      outgoing connections alive even if the client itself doesn't
#      support it.
#
#      You should also be aware that enabling this option increases
#      the likelihood of getting the "No server or forwarder data"
#      error message, especially if you are using a slow connection
#      to the Internet.
#
#      This option should only be used by experienced users who
#      understand the risks and can weight them against the benefits.
#
#  Examples:
#
#      connection-sharing 1
#
#connection-sharing 1
#
#
#  6.6. socket-timeout
#  ====================
#
#  Specifies:
#
#      Number of seconds after which a socket times out if no data
#      is received.
#
#  Type of value:
#
#      Time in seconds.
#
#  Default value:
#
#      None
#
#  Effect if unset:
#
#      A default value of 300 seconds is used.
#
#  Notes:
#
#      For SOCKS requests the timeout currently doesn't start until
#      the SOCKS server accepted the request. This will be fixed in
#      the next release.
#
#  Examples:
#
#      socket-timeout 300
#
socket-timeout 300
#
#
#  6.7. max-client-connections
#  ============================
#
#  Specifies:
#
#      Maximum number of client connections that will be served.
#
#  Type of value:
#
#      Positive number.
#
#  Default value:
#
#      None
#
#  Effect if unset:
#
#      Connections are served until a resource limit is reached.
#
#  Notes:
#
#      Privoxy creates one thread (or process) for every incoming
#      client connection that isn't rejected based on the access
#      control settings.
#
#      If the system is powerful enough, Privoxy can theoretically deal
#      with several hundred (or thousand) connections at the same time,
#      but some operating systems enforce resource limits by shutting
#      down offending processes and their default limits may be below
#      the ones Privoxy would require under heavy load.
#
#      Configuring Privoxy to enforce a connection limit below the
#      thread or process limit used by the operating system makes
#      sure this doesn't happen.  Simply increasing the operating
#      system's limit would work too, but if Privoxy isn't the only
#      application running on the system, you may actually want to
#      limit the resources used by Privoxy.
#
#      If Privoxy is only used by a single trusted user, limiting the
#      number of client connections is probably unnecessary. If there
#      are multiple possibly untrusted users you probably still want
#      to additionally use a packet filter to limit the maximal number
#      of incoming connections per client. Otherwise a malicious user
#      could intentionally create a high number of connections to
#      prevent other users from using Privoxy.
#
#      Obviously using this option only makes sense if you choose a
#      limit below the one enforced by the operating system.
#
#  Examples:
#
#      max-client-connections 256
#
#max-client-connections 256
#
#
#  6.8. handle-as-empty-doc-returns-ok
#  ====================================
#
#  Note:
#
#      This is a work-around for Firefox bug 492459: Websites are no
#      longer rendered if SSL requests for JavaScripts are blocked by
#      a proxy. (https:// bugzilla.mozilla.org/show_bug.cgi?id=492459)
#
#  Specifies:
#
#      The status code Privoxy returns for pages blocked with
#      +handle-as-empty-document.
#
#  Type of value:
#
#      0 or 1
#
#  Default value:
#
#      0
#
#  Effect if unset:
#
#      Privoxy returns a status 403(forbidden) for all blocked pages.
#
#  Effect if set:
#
#      Privoxy returns a status 200(OK) for pages blocked with
#      +handle-as-empty-document and a status 403(Forbidden) for all
#      other blocked pages.
#
#handle-as-empty-doc-returns-ok 0
#
#
#  7. WINDOWS GUI OPTIONS
#  =======================
#
#  Privoxy has a number of options specific to the Windows GUI
#  interface:
#
#
#  If "activity-animation" is set to 1, the Privoxy icon will animate
#  when "Privoxy" is active. To turn off, set to 0.
#
#activity-animation   1
#
#  If "log-messages" is set to 1, Privoxy will log messages to the
#  console window:
#
#log-messages   1
#
#  If "log-buffer-size" is set to 1, the size of the log buffer,
#  i.e. the amount of memory used for the log messages displayed in
#  the console window, will be limited to "log-max-lines" (see below).
#
#  Warning: Setting this to 0 will result in the buffer to grow
#  infinitely and eat up all your memory!
#
#log-buffer-size 1
#
#  log-max-lines is the maximum number of lines held in the log
#  buffer. See above.
#
#log-max-lines 200
#
#  If "log-highlight-messages" is set to 1, Privoxy will highlight
#  portions of the log messages with a bold-faced font:
#
#log-highlight-messages 1
#
#  The font used in the console window:
#
#log-font-name Comic Sans MS
#
#  Font size used in the console window:
#
#log-font-size 8
#
#  "show-on-task-bar" controls whether or not Privoxy will appear as
#  a button on the Task bar when minimized:
#
#show-on-task-bar 0
#
#  If "close-button-minimizes" is set to 1, the Windows close button
#  will minimize Privoxy instead of closing the program (close with
#  the exit option on the File menu).
#
#close-button-minimizes 1
#
#  The "hide-console" option is specific to the MS-Win console version
#  of Privoxy.  If this option is used, Privoxy will disconnect from
#  and hide the command console.
#
#hide-console
#
#

```

```

## Configuration file for a typical Tor user
## Last updated 12 April 2009 for Tor 0.2.1.14-rc.
## (May or may not work for much older or much newer versions of Tor.)
##
## Lines that begin with "## " try to explain what's going on. Lines
## that begin with just "#" are disabled commands: you can enable them
## by removing the "#" symbol.
##
## See 'man tor', or [https://www.torproject.org/tor-manual.html](https://www.torproject.org/tor-manual.html),
## for more options you can use in this file.
##
## Tor will look for this file in various places based on your platform:
## [https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#torrc](https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#torrc)


## Replace this with "SocksPort 0" if you plan to run Tor only as a
## relay, and not make any local application connections yourself.
SocksPort 9050 # what port to open for local application connections
SocksListenAddress 127.0.0.1 # accept connections only from localhost
SocksListenAddress 128.100.1.10:9050 # listen on this IP:port also

## Entry policies to allow/deny SOCKS requests based on IP address.
## First entry that matches wins. If no SocksPolicy is set, we accept
## all (and only) requests from SocksListenAddress.
#SocksPolicy accept 192.168.0.0/16
#SocksPolicy reject *
SocksPolicy accept *

## Logs go to stdout at level "notice" unless redirected by something
## else, like one of the below lines. You can have as many Log lines as
## you want.
##
## We advise using "notice" in most cases, since anything more verbose
## may provide sensitive information to an attacker who obtains the logs.
##
## Send all messages of level 'notice' or higher to /var/log/tor/notices.log
#Log notice file /var/log/tor/notices.log
## Send every possible message to /var/log/tor/debug.log
#Log debug file /var/log/tor/debug.log
## Use the system log instead of Tor's logfiles
#Log notice syslog
## To send all messages to stderr:
#Log debug stderr

## Uncomment this to start the process in the background... or use
## --runasdaemon 1 on the command line. This is ignored on Windows;
## see the FAQ entry if you want Tor to run as an NT service.
#RunAsDaemon 1

## The directory for keeping all the keys/etc. By default, we store
## things in $HOME/.tor on Unix, and in Application Data\tor on Windows.
#DataDirectory /var/lib/tor

## The port on which Tor will listen for local connections from Tor
## controller applications, as documented in control-spec.txt.
#ControlPort 9051
## If you enable the controlport, be sure to enable one of these
## authentication methods, to prevent attackers from accessing it.
#HashedControlPassword 16:872860B76453A77D60CA2BB8C1A7042072093276A3D701AD684053EC4C
#CookieAuthentication 1

############### This section is just for location-hidden services ###

## Once you have configured a hidden service, you can look at the
## contents of the file ".../hidden_service/hostname" for the address
## to tell people.
##
## HiddenServicePort x y:z says to redirect requests on port x to the
## address y:z.

#HiddenServiceDir /var/lib/tor/hidden_service/
#HiddenServicePort 80 127.0.0.1:80

#HiddenServiceDir /var/lib/tor/other_hidden_service/
#HiddenServicePort 80 127.0.0.1:80
#HiddenServicePort 22 127.0.0.1:22

################ This section is just for relays #####################
#
## See [https://www.torproject.org/docs/tor-doc-relay](https://www.torproject.org/docs/tor-doc-relay) for details.

## Required: what port to advertise for incoming Tor connections.
#ORPort 9001
## If you want to listen on a port other than the one advertised
## in ORPort (e.g. to advertise 443 but bind to 9090), uncomment the
## line below too. You'll need to do ipchains or other port forwarding
## yourself to make this work.
#ORListenAddress 0.0.0.0:9090

## A handle for your relay, so people don't have to refer to it by key.
#Nickname ididnteditheconfig

## The IP address or full DNS name for your relay. Leave commented out
## and Tor will guess.
#Address noname.example.com

## Define these to limit how much relayed traffic you will allow. Your
## own traffic is still unthrottled. Note that RelayBandwidthRate must
## be at least 20 KBytes.
#RelayBandwidthRate 100 KBytes  # Throttle traffic to 100KB/s (800Kbps)
#RelayBandwidthBurst 200 KBytes # But allow bursts up to 200KB/s (1600Kbps)

## Contact info to be published in the directory, so we can contact you
## if your relay is misconfigured or something else goes wrong. Google
## indexes this, so spammers might also collect it.
#ContactInfo Random Person <nobody AT example dot com>
## You might also include your PGP or GPG fingerprint if you have one:
#ContactInfo 1234D/FFFFFFFF Random Person <nobody AT example dot com>

## Uncomment this to mirror directory information for others. Please do
## if you have enough bandwidth.
#DirPort 9030 # what port to advertise for directory connections
## If you want to listen on a port other than the one advertised
## in DirPort (e.g. to advertise 80 but bind to 9091), uncomment the line
## below too. You'll need to do ipchains or other port forwarding yourself
## to make this work.
#DirListenAddress 0.0.0.0:9091
## Uncomment to return an arbitrary blob of html on your DirPort. Now you
## can explain what Tor is if anybody wonders why your IP address is
## contacting them. See contrib/tor-exit-notice.html for a sample.
#DirPortFrontPage /etc/tor/exit-notice.html

## Uncomment this if you run more than one Tor relay, and add the identity
## key fingerprint of each Tor relay you control, even if they're on
## different networks. You declare it here so Tor clients can avoid
## using more than one of your relays in a single circuit. See
## [https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#MultipleServers](https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#MultipleServers)
#MyFamily $keyid,$keyid,...

## A comma-separated list of exit policies. They're considered first
## to last, and the first match wins. If you want to _replace_
## the default exit policy, end this with either a reject *:* or an
## accept *:*. Otherwise, you're _augmenting_ (prepending to) the
## default exit policy. Leave commented to just use the default, which is
## described in the man page or at
## [https://www.torproject.org/documentation.html](https://www.torproject.org/documentation.html)
##
## Look at [https://www.torproject.org/faq-abuse.html#TypicalAbuses](https://www.torproject.org/faq-abuse.html#TypicalAbuses)
## for issues you might encounter if you use the default exit policy.
##
## If certain IPs and ports are blocked externally, e.g. by your firewall,
## you should update your exit policy to reflect this -- otherwise Tor
## users will be told that those destinations are down.
##
#ExitPolicy accept *:6660-6667,reject *:* # allow irc ports but no more
#ExitPolicy accept *:119 # accept nntp as well as default exit policy
#ExitPolicy reject *:* # no exits allowed
#
## Bridge relays (or "bridges") are Tor relays that aren't listed in the
## main directory. Since there is no complete public list of them, even if an
## ISP is filtering connections to all the known Tor relays, they probably
## won't be able to block all the bridges. Also, websites won't treat you
## differently because they won't know you're running Tor. If you can
## be a real relay, please do; but if not, be a bridge!
#BridgeRelay 1
#ExitPolicy reject *:*


```

---

### Post by bodhi.zazen on 2010-09-01
Other then the obvious question, why ? Why would someone connect to your apache server to use TOR ? ...

As I indicated, typically people run TOR locally as opposed to a central server of some kind.

If you want, you can configure privoxy to accept connections, I still do not understand why you feel you need apache at all. I can not tell if apache is serving some purpose here or if you are not understanding how to configure privoxy.

you want your proxies to go how ?


firefox -> apache on your server -> privoxy -> TOR ?

You have done what I asked you not to do, you dumped the entire privoxy config files.

Please post only the relevant sections, the things you changed.

How did you configure apache ?

The only obvious thing I see is that you did not configure privoxy to use TOR.

---

### Post by pehden on 2010-09-01
> **bodhi.zazen said:**
> 
firefox -> apache on your server -> privoxy -> TOR

How did you configure apache ?

The only obvious thing I see is that you did not configure privoxy to use TOR.


firefox -> apache on server ->privoxy-> tor
 is what im running.

Sorry bout that i didnt read all of the post the time you said that 
  here is the apache conf only the part that i changed 

```

<VirtualHost *:80>
	ServerAdmin 
	ServerName t	
	SetEnvIf Request_URI "^/u" dontlog
	Loglevel warn
	ProxyRequests Off
	<Proxy *>
		allow from all
	</Proxy>
		ProxyPass /  http://
		ProxyPassReverse /  http://
</VirtualHost>

```

---

### Post by bodhi.zazen on 2010-09-01
> **pehden said:**
> firefox -> apache on server ->privoxy-> tor
 is what im running.

Sorry bout that i didnt read all of the post the time you said that 
  here is the apache conf only the part that i changed 

```

<VirtualHost *:80>
    ServerAdmin xxx
    ServerName xxx
    SetEnvIf Request_URI "^/u" dontlog
    Loglevel warn
    ProxyRequests Off
    <Proxy *>
        allow from all
    </Proxy>
        ProxyPass /  http://127.1.0.1:9050/
        ProxyPassReverse /  http://127.1.0.1:9050/
</VirtualHost>

```

That proxypass statement points to TOR not privoxy. Also you have proxy requests set to off, that just sounds wrong for what you are wanting to do. I am not sure exactly what you expect apache to do, and I am not sure it will function the way you intend. Hard to say from what you have posted.

This site has specific step-by step instructions

[http://www.torproject.org/docs/debian.html.en](http://www.torproject.org/docs/debian.html.en)

After performing step one, click step 2

Which points to this page

[http://www.torproject.org/docs/tor-doc-unix.html.en#polipo](http://www.torproject.org/docs/tor-doc-unix.html.en#polipo)

You need to read the privoxy page

[https://trac.torproject.org/projects/tor/wiki/TheOnionRouter/PrivoxyConfig](https://trac.torproject.org/projects/tor/wiki/TheOnionRouter/PrivoxyConfig)

I would not use that privoxy config file, just read the file and make the changes.

---

### Post by pehden on 2010-09-02
so apache need to point to what?

---

### Post by bodhi.zazen on 2010-09-02
> **pehden said:**
> so apache need to point to what?

You answered this question in your earlier post :

> **pehden said:**
> firefox -> apache on server ->privoxy-> tor

As I keep telling you , I do not think you need apache, you can go direct

firefox -> privoxy -> tor

Usually people do this on the client, but you can do this server side as well.

I think you :

1. Do not understand how to set up proxies.

2. Are making this harder then it needs to be.

3. Are probably using the wrong tool for the task at hand. You almost certainly want to use VPN or ssh.

---

### Post by pehden on 2010-09-02
> **bodhi.zazen said:**
> You answered this question in your earlier post :



As I keep telling you , I do not think you need apache, you can go direct

firefox -> privoxy -> tor

Usually people do this on the client, but you can do this server side as well.

I think you :

1. Do not understand how to set up proxies.

2. Are making this harder then it needs to be.

3. Are probably using the wrong tool for the task at hand. You almost certainly want to use VPN or ssh.

I am doing this set up for a reason, I have squid set up for something else, Apache 80 is the only port I want to open for what I am wanting to do.
I have done the ssh tunnel already to I use that for another purpose. I would go direct but to programs cant share a port. So I need apache two proxy the info to/from tor.

---

### Post by bodhi.zazen on 2010-09-02
> **pehden said:**
> I am doing this set up for a reason, I have squid set up for something else, Apache 80 is the only port I want to open for what I am wanting to do.
I have done the ssh tunnel already to I use that for another purpose. I would go direct but to programs cant share a port. So I need apache two proxy the info to/from tor.

OK, point apache at privoxy and privoyx at TOR and hope it works.

---

### Post by pehden on 2010-09-02
> **bodhi.zazen said:**
> OK, point apache at privoxy and privoyx at TOR and hope it works.

Ok so what port does apache need to look at? The 8118 or 9050?

And what did I do wrong on my Conf for privoxy

---

### Post by bodhi.zazen on 2010-09-02
> **pehden said:**
> Ok so what port does apache need to look at? The 8118 or 9050?

And what did I do wrong on my Conf for privoxy

You can configure all these to use any port you like.

By default privoxy uses port 8118 and TOR 9050.

The configuration is in the links I have given you, have you not read the links ? Once again, you will need to point apache to privoxy and privoxy to tor.

---

### Post by rollin on 2010-09-02
> **bodhi.zazen said:**
> You can configure all these to use any port you like.

By default privoxy uses port 8118 and TOR 9050.

The configuration is in the links I have given you, have you not read the links ? Once again, you will need to point apache to privoxy and privoxy to tor.

You must have some kind of "divine" patience! None of this makes sense. Why would you anonymize the outbound connections of an apache server? Depending on the content this also puts the people connected at risk from leaks of information.

---

### Post by pehden on 2010-10-12
The reason i was trying to do this didnt work as i would have liked so I backed off.


I was wanting to make a spider that crawled via proxy to test a theory of mine but I didnt get around to getting it to actually run the way I wanted and instead decided to not do it.

---

### Post by pehden on 2010-11-15
Hey on post #12 can you delete the email and the domain.

---

### Post by bodhi.zazen on 2010-11-16
> **pehden said:**
> Hey on post #12 can you delete the email and the domain.

done =)

---

### Post by pehden on 2010-11-16
> **bodhi.zazen said:**
> done =)

Thanks

---

