---
title: "Rdac"
date: 2011-01-06
forum: Server Platforms
---

### Post by mboeschen on 2011-01-06
I am trying to connect a Dell Powervault MD3200i to Ubuntu 10.10.  It appears that it needs support for RDAC for multipath, but it is my understanding this module/driver is not loaded.
How can I get RDAC support loaded in Ubuntu?

---

### Post by mboeschen on 2011-01-20
Anybody even have any idea where to start?

---

### Post by mboeschen on 2011-01-20
Anybody even have any idea where to start?

---

### Post by ecsedi on 2011-01-20
Maybe you should simply load scsi_dh_rdac module into the kernel with

[FONT=Courier New]**modprobe scsi_dh_rdac**[/FONT]

After that you must create a /etc/multipath.conf file as recommended by DELL:
[FONT=Courier New][B]
defaults {
  max_fds             8192
  user_friendly_names yes
}

blacklist {[/B][B]
  device {
    vendor  "*"
    product "Universal Xport"
  }
}

devices {[/B][B]
  device {
    vendor               "DELL"
    product              "MD32xxi"
    path_grouping_policy group_by_prio
    prio                 rdac
    polling_interval     5
    path_checker         rdac
    path_selector        "round-robin 0"
    hardware_handler     "1 rdac"
    failback             immediate
    features             "2 pg_init_retries 50"
    no_path_retry        30
    rr_min_io            100
    prio_callout         "/sbin/mpath_prio_rdac /dev/%n"
  }

[/B][B]   device {
    vendor               "DELL"
    product              "MD32xx"
    path_grouping_policy group_by_prio
    prio                 rdac
    polling_interval     5
    path_checker         rdac
    path_selector        "round-robin 0"
    hardware_handler     "1 rdac"
    failback             immediate
    features             "2 pg_init_retries 50"
    no_path_retry        30
    rr_min_io            100
    prio_callout         "/sbin/mpath_prio_rdac /dev/%n"
  }
}[/B][/FONT]   

Then multipathd must be restarted with

[FONT=Courier New]**/etc/init.d/multipath-tools restart**[/FONT]

Hope that helps. It worked for me at least.

Regards, Cornelius

---

