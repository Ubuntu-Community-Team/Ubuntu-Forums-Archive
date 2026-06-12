---
title: "Snort stopped working"
date: 2011-07-02
forum: Security
---

### Post by Cap_Sot on 2011-07-02
Hello,
I'm running Ubuntu 11.04 and I upgraded Snort recently to version 2.9.0.5..When I updated the rules, some error messages came up..After I changed the paths of the rule files and the dynamicpreprocessor, another strange error came up and snort isn't running:

ERROR: /etc/snort/snort.conf(250) => Unknown Stream5 global option (max_active_responses 2)
Fatal Error, Quitting..

Any ideas what could be causing this error?

---

### Post by Dangertux on 2011-07-02
This is happening because the version you have installed was not compiled with 

./configure --enable-enable-active-response / -DACTIVE_RESPONSE

However, the conf file you are using still contains information about sending active responses when a connection is dropped (IE : TCP RST). The most effective way I've found to fix this is to install snort from the source. Additionally you can try commenting out the active_response lines in the snort.conf, this is iffy and usually won't work  though YMMV.

Consult the snort manpages for more info on this.

Good luck

---

### Post by Cap_Sot on 2011-07-03
Thank you for your reply!
I tried commenting out the lines in snort.conf where those errors were appearing and then tried to run:

sudo snort -c /etc/snort/snort.conf

The output indicates that the initialization of Snort is complete:



        --== Initialization Complete ==--

   ,,_     -*> Snort! <*-
  o"  )~   Version 2.9.0.5 (Build 135) 
   ''''    By Martin Roesch & The Snort Team: [http://www.snort.org/snort/snort-team](http://www.snort.org/snort/snort-team)
           Copyright (C) 1998-2011 Sourcefire, Inc., et al.
           Using libpcap version 1.1.1
           Using PCRE version: 8.12 2011-01-15

           Rules Engine: SF_SNORT_DETECTION_ENGINE  Version 1.13 <Build 18>
           Preprocessor Object: SF_FTPTELNET  Version 1.2  <Build 13>
           Preprocessor Object: SF_SMTP  Version 1.1  <Build 9>
           Preprocessor Object: SF_SDF  Version 1.1  <Build 1>
           Preprocessor Object: SF_DCERPC2  Version 1.0  <Build 3>
           Preprocessor Object: SF_DNS  Version 1.1  <Build 4>
           Preprocessor Object: SF_SSH  Version 1.1  <Build 3>
           Preprocessor Object: SF_SSLPP  Version 1.1  <Build 4>
Commencing packet processing (pid=4568)

But when i typed a simple ps command to see if snort is running:

sudo ps -A | grep snort

what i got is nothing..Also tried to start snort with the following command:

sudo /etc/init.d/snort start

but the answer is negative once again:

 * Starting Network Intrusion Detection System  snort      [fail]

what could cause such a failure?

---

### Post by Dangertux on 2011-07-03
> **Cap_Sot said:**
> Thank you for your reply!
I tried commenting out the lines in snort.conf where those errors were appearing and then tried to run:

sudo snort -c /etc/snort/snort.conf

The output indicates that the initialization of Snort is complete:



        --== Initialization Complete ==--

   ,,_     -*> Snort! <*-
  o"  )~   Version 2.9.0.5 (Build 135) 
   ''''    By Martin Roesch & The Snort Team: [http://www.snort.org/snort/snort-team](http://www.snort.org/snort/snort-team)
           Copyright (C) 1998-2011 Sourcefire, Inc., et al.
           Using libpcap version 1.1.1
           Using PCRE version: 8.12 2011-01-15

           Rules Engine: SF_SNORT_DETECTION_ENGINE  Version 1.13 <Build 18>
           Preprocessor Object: SF_FTPTELNET  Version 1.2  <Build 13>
           Preprocessor Object: SF_SMTP  Version 1.1  <Build 9>
           Preprocessor Object: SF_SDF  Version 1.1  <Build 1>
           Preprocessor Object: SF_DCERPC2  Version 1.0  <Build 3>
           Preprocessor Object: SF_DNS  Version 1.1  <Build 4>
           Preprocessor Object: SF_SSH  Version 1.1  <Build 3>
           Preprocessor Object: SF_SSLPP  Version 1.1  <Build 4>
Commencing packet processing (pid=4568)

But when i typed a simple ps command to see if snort is running:

sudo ps -A | grep snort

what i got is nothing..Also tried to start snort with the following command:

sudo /etc/init.d/snort start

but the answer is negative once again:

 * Starting Network Intrusion Detection System  snort      [fail]

what could cause such a failure?

A possibly incomplete or incorrect config file, like I said commenting those lines alone may not do it. Likely you will have to generate a configuration file without active_response or recompile snort to support active response.

---

