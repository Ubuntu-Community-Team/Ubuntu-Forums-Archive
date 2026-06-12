---
title: "VMWare Server Remote Administration Site."
date: 2008-10-20
forum: Virtualisation
---

### Post by thefatmoop on 2008-10-20
I was able to install vmware server and get the local web vm administration working. I am unable to connect over a network (same subnet/network) to the vmware server web administration page. 

since in the final install vmware server will be installed on an ubuntu server... So I need to make sure i can simply login to the web vmware admin site. 

IP addresses 
virtual machine - ends in .140

desktop with vmserver installed - ends in .101

laptop - ends in .104 


the site "https://192.168.1.101:8333/ui/#" only works on the machine with vmware server installed 


what am I doing wrong? How would I connect to the web administration if I was running wmware server on a headless ubuntu server?

---

### Post by thefatmoop on 2008-10-20
when I say "it doesn't work" i mean I go to the site and it's just a blank page. my laptop (remote web manager) is running firefox/ubuntu 8.04 

the browser is just blank with a "loading" but it's not loading anything. Already told it to go ahead and use the insecure SSL cert

---

### Post by thefatmoop on 2008-10-20
tried it on a windows vista machine using IE and it worked... tried it from another ubuntu box on firefox and same error with "done" yet blank page..

---

### Post by thefatmoop on 2008-10-20
bump

---

### Post by thefatmoop on 2008-10-21
bump

---

### Post by fduff on 2009-04-14
I've installed **VMware server 2.0.1** today on **ubuntu 8.04** on a remote machine (without screen) and same issue, whilst trying to access remotely the wmware web config page, I kept getting a **blank page on FireFox3**.

Saw your post, then tried to access ```
https://192.168.1.101:8333/ui
``` from IE 7 and it worked straight away! :-k

IE actually added a '**/#**' at the end of that URL, to become ```
https://192.168.1.101:8333/ui**/#**
```

so I tried the exact same URL from FF3 and then it worked fine! ](*,)
and this time from FF in both Ubunbu and winXP. 

the FF error console showed many errors at that moment, some declaration errors in some .properties files: ```

/* File 1 */
new Object({
   // units
   common_unit_bytes: "BYTES",
   common_unit_kb: "KB",
   common_unit_mb: "MB",
   common_unit_gb: "GB",
   common_unit_tb: "TB",

   common_unit_pb: "PB"
});

/* File 2 */
new Object({
   // OptionPane resources.
   OptionPane_yes: "Yes",
   OptionPane_no: "No",
   OptionPane_ok: "OK",

   OptionPane_cancel: "Cancel",

   install_plugin: "Install plug-in",
   install_help: "Click here for installation instructions",
   installing: "Follow your browser's installation procedure.",

   install: "Install",
   help: "Help",

   status_success: "Successfully installed.",
   status_user_canceled: "Installation canceled.",
   status_access_denied: "The plug-in cannot be installed because you are not " +

      "authorized to install it. Please try again using an authorized " +
      "account such as 'administrator' or 'root', or contact your system " +
      "administrator for help.",

   status_reboot_needed: "Browser restart required after plug-in installation.",
   status_default: "The plug-in could not be installed. (Error: {0}) Please try again."

});

...

```


So, could it be that FF3 didnt manage to interpret the buggy *url/js code* on that page and caused it to stop loading it...

---

### Post by senor_smile on 2009-12-28
I am having the same problems as previously described by the OP.  I can access the web access from [http://localhost:8222/ui/](http://localhost:8222/ui/) on the machine where vmware server 2 is installed.  I can't access [https://localhost:8333/ui/](https://localhost:8333/ui/) on the local machine.  It gives me a blank page and says loading in the toolbar.  If I try to access the IP address from any other machine, it forces a redirect to the https page and gives me the same blank page.  I.E. tried [http://192.168.5.18:8222/ui/](http://192.168.5.18:8222/ui/) which redirects to [https://192.168.5.18:8333/ui/](https://192.168.5.18:8333/ui/)).  Please, any one with any info on getting the vmware https console working over the network?

---

