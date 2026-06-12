---
title: "Jabber-MUC and Jabberd2 Router Not Communicating"
date: 2013-12-07
forum: Server Platforms
---

### Post by Kirk Schnable on 2013-12-07
I've been trying to get Jabber-MUC working on my XMPP server for awhile.  I've installed both of them from the repository on Ubuntu 12.04, so here are my versions:

(from dpkg --list | grep jabber)
```
ii  jabber-muc                        0.8-3                               Multi User Conference component for the Jabber IM server
ii  jabberd2                          2.2.8-2.2ubuntu0.12.04.1            Jabber instant messenger server
```

I've isolated some parts of the configuration which are relevant.  From /etc/jabberd2/router.xml:
[QUOTE="router.xml"]<!-- Local network configuration -->
  <local>
    <!-- IP address to bind to (default: 0.0.0.0) -->
    <ip>0.0.0.0</ip>


    <!-- Port to bind to (default: 5347) -->
    <port>5347</port>


    <!-- File containing the user table. This is where the router gets
         its component and secret information from for component
         authentication.-->
    <users>/etc/jabberd2/router-users.xml</users>


    <!-- Shared secret used to identify XEP-0114 components (that is,
         "jabber:component:accept" components that authenticate using
         the Jabber Component Protocol's "handshake", for example
         mu-conference). If this is commented out, support for XEP-0114
         components will be disabled. -->
    <secret>matching-secret</secret>

    <!-- File containing an SSL certificate and private key for client         connections. From SSL_CTX_use_certificate_chain_file(3):
         "The certificates must be in PEM format and must be sorted
         starting with the subject's certificate (actual client or
         server certificate), followed by intermediate CA certificates
         if applicable, and ending at the highest level (root) CA"
         (the latter one being optional).
         If this is commented out, connecting components will not be able
         to request an SSL-encrypted channel. -->


    <pemfile>/etc/jabberd2/server.pem</pemfile>


  </local>[/QUOTE]

From /etc/jabberd2/muc.xml:
[QUOTE="muc.xml"]
  <ip>127.0.0.1</ip> <!-- address of the jabber server -->
  <port>5347</port>  <!-- port used to connect the service to the jabber server -->
  <secret>matching-secret</secret> <!-- secret shared with the jabber server -->
  <pemfile>/etc/jabberd2/server.pem</pemfile> 
  <spool>/var/spool/jabber-muc/rooms/</spool> <!-- directory containing the rooms data -->
  <logdir>/var/log/jabberd2/</logdir> <!-- directory containing the debug log (the file is called mu-conference.log) -->
  <pidfile>/var/run/jabberd2/muc.pid</pidfile> <!-- file that will contain the PID of the process -->
  <loglevel>255</loglevel> <!-- log verbosity, 255 for very verbose, 0 for quiet -->
[/QUOTE]

In muc.xml, I added the <pemfile> directive.  I'm not sure if it's valid or not, but having it doesn't affect the symptoms at all.

Upon issuing **sudo service jabberd2 restart muc**, the following entries are made to my logs:

[QUOTE="router.log"]
Sat Dec  7 17:36:25 2013 [notice] [127.0.0.1, port=36722] connect
Sat Dec  7 17:36:25 2013 [notice] [127.0.0.1, port=36722] disconnect
Sat Dec  7 17:36:32 2013 [notice] [127.0.0.1, port=36723] connect
Sat Dec  7 17:36:32 2013 [notice] [127.0.0.1, port=36723] disconnect
[/QUOTE]

[QUOTE="mu-conference.log"]
Sat Dec  7 17:36:25 2013 main.c:168 (main): Jabber Component Runtime -- 0.2.4  starting.
Sat Dec  7 17:36:25 2013 MU-Conference: [conference.c:1076 (conference)] mu-conference loading  - Service ID: conference.mydomain.com
Sat Dec  7 17:36:25 2013 MU-Conference: [conference.c:1082 (conference)] Malloc: _cni=136
Sat Dec  7 17:36:25 2013 MU-Conference: [conference.c:1157 (conference)] Adding sadmin 
        
Sat Dec  7 17:36:25 2013 MU-Conference: [conference.c:1157 (conference)] Adding sadmin [EMAIL="admin@mydomain.com"]admin@mydomain.com[/EMAIL]
Sat Dec  7 17:36:25 2013 MU-Conference: [conference.c:1157 (conference)] Adding sadmin 
      
Sat Dec  7 17:36:25 2013 MU-Conference: [xdb.c:319 (xdb_rooms_get)] asked to get rooms from xdb 
Sat Dec  7 17:36:25 2013 MU-Conference: [xdb.c:418 (xdb_rooms_get)] skipping .. no results
Sat Dec  7 17:36:25 2013 jcr_xdb.c:69 (xdb_set): xdb_set: rc == 1
Sat Dec  7 17:36:25 2013 main.c:219 (main): Main loop starting.
Sat Dec  7 17:36:25 2013 jcr_base_connect.c:34 (jcr_socket_connect): Attempting connection to 127.0.0.1:5347
Sat Dec  7 17:36:25 2013 jcr_base_connect.c:87 (jcr_send_start_stream): Opening XML stream: sent 175 bytes
Sat Dec  7 17:36:25 2013 jcr_main_stream_error.c:50 (jcr_main_new_stream): Server stream connected.
Sat Dec  7 17:36:25 2013 jcr_main_stream_error.c:50 (jcr_main_new_stream): packet delivery thread starting.
Sat Dec  7 17:36:25 2013 jcr_deliver.c:93 (jcr_queue_deliver): wrote 1 packets of 63 bytes
Sat Dec  7 17:36:25 2013 jcr_elements.c:178 (jcr_read_data): Main Channel Error: rc=2
Sat Dec  7 17:36:25 2013 jcr_main_stream_error.c:56 (jcr_main_close_stream): Server stream error, resetting
Sat Dec  7 17:36:30 2013 jcr_deliver.c:101 (jcr_queue_deliver): packet delivery thread exiting.
Sat Dec  7 17:36:30 2013 jcr_deliver.c:102 (jcr_queue_deliver):   Last DvryQ Buffer=''
Sat Dec  7 17:36:32 2013 jcr_base_connect.c:34 (jcr_socket_connect): Attempting connection to 127.0.0.1:5347
Sat Dec  7 17:36:32 2013 jcr_deliver.c:51 (jcr_queue_deliver): packet delivery thread starting.
Sat Dec  7 17:36:32 2013 jcr_base_connect.c:87 (jcr_send_start_stream): Opening XML stream: sent 175 bytes
Sat Dec  7 17:36:32 2013 jcr_main_stream_error.c:50 (jcr_main_new_stream): Server stream connected.
Sat Dec  7 17:36:32 2013 jcr_deliver.c:93 (jcr_queue_deliver): wrote 1 packets of 63 bytes
Sat Dec  7 17:36:32 2013 jcr_elements.c:178 (jcr_read_data): Main Channel Error: rc=2
Sat Dec  7 17:36:32 2013 jcr_main_stream_error.c:56 (jcr_main_close_stream): Server stream error, resetting
Sat Dec  7 17:36:37 2013 jcr_deliver.c:101 (jcr_queue_deliver): packet delivery thread exiting.
Sat Dec  7 17:36:37 2013 jcr_deliver.c:102 (jcr_queue_deliver):   Last DvryQ Buffer=''
[/QUOTE]

Any idea what the issue might be?  As far as I can tell, I have everything configured correctly.  I have a Jitsi Videobridge which is connecting to the router successfully using the XEP-0114 shared secret, so I know that things in general are working, I believe the problem is with MUC or my MUC configuration.

I can provide more information if necessary, just let me know what you'd like to see.  Anybody else experience this problem before?

Thanks,
Kirk

---

### Post by Kirk Schnable on 2014-01-10
Just as an update, I tried compiling MUC version 0.7 from source this morning, and followed the guide on the Jabberd2 wiki:  [https://github.com/jabberd2/jabberd2/wiki/InstallGuide-MU-Conferencing](https://github.com/jabberd2/jabberd2/wiki/InstallGuide-MU-Conferencing)

I am running into the same errors and difficulties with version 0.7.

I really don't understand how anyone with jabberd2 has the MUC component working.  Any insights would be appreciated!

---

### Post by Kirk Schnable on 2014-01-10
I think I figured out what was wrong.  I'm not at all thrilled\happy about the solution, but I am happy that things are working.

My XEP secret was apparently too long?  I shortened the XEP secret and it immediately connected up and started working...  After re-lengthening the XEP secret as a test, it did the same thing again.

So if anyone else runs into this, try a shorter XEP secret.  Maybe test with a secret like "testing" and create a better secret from there until it breaks.

---

### Post by Habitual on 2014-01-13
Hey Kirk:
How "long" is|was "too long" on the secret?

---

### Post by Kirk Schnable on 2014-01-13
> **Habitual said:**
> Hey Kirk:
How "long" is|was "too long" on the secret?
I haven't done that much thorough testing to find the cut-off number.  I am planning on doing some testing and doing a full start-to-finish write-up and posting it on my tech blog since I found throughout setting up Jabberd2\MUC that the documentation I needed was sparse, and in some cases non-existent.

I can tell you for sure that 10 character secrets are working for me.  My secret from before was around 18-20 characters and was too long.

---

### Post by Habitual on 2014-01-13
> **Kirk Schnable said:**
> posting it on my tech blog... url? or pm me the site, if available to the public?
Thanks!

Found it. ;)

---

### Post by Kirk Schnable on 2014-01-13
> **Habitual said:**
> url? or pm me the site, if available to the public?
Thanks!

Found it. ;)
I have not written the aforementioned blog post yet, but it's on my list of things to do try to get done today.

---

