---
title: "Apparmor profile for Apache2 mpm_event + php5-fpm"
date: 2015-02-25
forum: Security
---

### Post by watersevenub on 2015-02-25
Hi. 

I've been using apparmor with apache2 prefork+mod_php for a few months now and all goes well. The problem is, I'm switching to apache2 mpm_event and php5-fpm and apparmor causes problems, it seems php is not interpreted. In fact, in the beggining of the profile usr.sbin.apache2, its original author Marc says the following:

  # 2- Load the mpm_prefork and mod_apparmor modules:
  #    sudo a2dismod <other non-prefork mpm>
  #    sudo a2enmod mpm_prefork
  #    sudo a2enmod apparmor
  #    sudo service apache2 restart

So, will it not work with mpm_event in the first place? Why? What changes are necessary? Any ideas? Thanks.

> ==== usr.sbin.apache2

 #include <abstractions/base>
  #include <abstractions/nameservice>

  capability dac_override,
  capability kill,
  capability net_bind_service,
  capability setgid,
  capability setuid,
  capability sys_tty_config,

  / rw,
  /** mrwlkix,
  signal (send) peer=/usr/sbin/apache2//*,


  ^DEFAULT_URI {
    #include <abstractions/base>
    #include <abstractions/nameservice>

    / rw,
    /** mrwlkix,
    signal (receive) peer=/usr/sbin/apache2,
  }

  ^HANDLING_UNTRUSTED_INPUT {
    #include <abstractions/nameservice>

    / rw,
    /** mrwlkix,
    signal (receive) peer=unconfined,
    signal (receive) peer=/usr/sbin/apache2,
    signal peer=@{profile_name},

  }

  # This directory contains web application
  # package-specific apparmor files.

  #include <apache2.d>

  # Site-specific additions and overrides. See local/README for details.
  #include <local/usr.sbin.apache2>
}

==== abstractions/apache2-common
# vim:syntax=apparmor

# This file contains basic permissions for Apache and every vHost

  #include <abstractions/nameservice>

  # Apache
  network inet stream,
  network inet6 stream,
  # apache manual, error pages and icons
  /usr/share/apache2/** r,

  # changehat itself
  @{PROC}/@{pid}/attr/current                        rw,

  # htaccess files - for what ever it is worth
  /**/.htaccess            r,

  /dev/urandom            r,

  signal (receive) peer=unconfined,
  signal (receive) peer=/usr/sbin/apache2,
  signal peer=@{profile_name},

====== The main website profile includes 
  #include <abstractions/apache2-common>
  #include <abstractions/php5>

And other common permissions which should not cause any issue. 

---

