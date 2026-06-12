---
title: "Setting up shakespeer backend"
date: 2006-07-15
forum: The Cafe
---

### Post by kson on 2006-07-15
Introduction
[INDENT]Shakespeer is a brilliant direct connect client for macosx and is built with a client server architecture and is open source. The fine part of this is that the program compiles on any *nix system (except the aqua gui). That means you can run the backend on your linuxbox and the gui on your mac.[/INDENT] 

Why?
[INDENT]Why is this interesting? you ask. I have a powerbook and an ubuntubox. Because there are no good dc-clients for linux and Shakespeer is a great one, I rather use Shakespeer. [/INDENT]

And?
[INDENT]Unfortunately, all my home recorded videos and music is ofcourse on the linuxbox. That means when I´m hashing my share, all data should be transferred to the laptop and then hashed. Same thing with uploading, data flowing from the server to the laptop and the same data from the laptop to the internet.[/INDENT]

How?
[INDENT]I solved this by running the backend on the linuxbox and connecting to it from the laptop. It´s the backend thats doing all the work so I can even shutdown my mac without interrupting my downloads.[/INDENT]

Can I do it?
[INDENT]This isn´t complicated at all and should take a half hour or so when you know how to do it but thats the tricky part. Allmost no documentation is written about this. Thats why I´m thinking of writing a tutorial or a howto.[/INDENT]

Question:
[INDENT]Is anyone interested in this and can someone help me writing it?[/INDENT]

Best regards /Martin

---

### Post by kson on 2006-10-23
The current released version is 0.9.2 and very old but you can find snapshots here: [http://shakespeer.bzero.se/snapshots/](http://shakespeer.bzero.se/snapshots/) . Download and unpack. Compile the backend by just typing "make" in the shakespeer directory. It will probably download Berkeley DB and compile it to. There are more dependencies but Im really not sure of which. My compile ends with errors with libconfuse in the cli directory. Dont mind that because the backend is already compiled and ready for use. Move sphubd/sphubd and sphubd/sphashd to /usr/bin (or similar). I have written a script for starting the backend because you need a working directory for it, it saves database and stuff there: 

```
sphubd -w <working directory> -p <port number>
```

All settings comes from the mac so open ~/library/preferences/se.hedenfalk.shakespeer.plist with property list editor and enter your settings there, remember you have to use pathways for the server so the download directory should be something on the backend not the frontend.

Start the server, check if the backend is running by typing:
```
ps -e
``` and look for one sphubd and two sphashd, one of them will probably have a tag <defunc>, dunno why but it works anyway. Start the front end and type in ipnr and portnr in the advanced settings and you are good to go!

Viewing users share doesn´t work, but you can click "download all files in directory"

One more important thing, you have to have the exact same version on the backend and frontend. Im using the latest snapshot because it has a fix for hashing big files on linux and then I dont have to compile the whole program on the mac as with the darcs version.

Hope it helps!

---

### Post by skruiper on 2006-10-25
Hi Martin,

I'm stuck, first I tried the 0.9.2 version of Shakespeer which didn't have a good makefile

after some searching I found updated tarballs at [http://shakespeer.bzero.se/snapshots/](http://shakespeer.bzero.se/snapshots/)

When I try to make from the sphubd dir I get a lot of errors:
> [SIZE=1]~/shakespeer-20061007/sphubd$ sudo make
awk -f ../support/gen_cmd_source.awk ../sphubd/sphashd_cmd.in > sphashd_cmd.c
awk -f ../support/gen_cmd_header.awk ../sphubd/sphashd_cmd.in > sphashd_cmd.h
awk -f ../support/gen_cmd_source.awk ../sphubd/ui_cmd.in > ui_cmd.c
awk -f ../support/gen_cmd_header.awk ../sphubd/ui_cmd.in > ui_cmd.h
awk -f ../support/gen_send_source.awk ../spclient/spclient_cmd.in > ui_send.c
awk -f ../support/gen_send_header.awk ../spclient/spclient_cmd.in > ui_send.h
awk -f ../support/gen_send_source.awk ../sphubd/sphashd_client_cmd.in > sphashd_send.c
awk -f ../support/gen_send_header.awk ../sphubd/sphashd_client_cmd.in > sphashd_send.h
awk -f ../support/gen_cmd_source.awk ../sphubd/sphashd_client_cmd.in > sphashd_client_cmd.c
awk -f ../support/gen_cmd_header.awk ../sphubd/sphashd_client_cmd.in > sphashd_client_cmd.h
awk -f ../support/gen_send_source.awk ../sphubd/sphashd_cmd.in > sphashd_client_send.c
awk -f ../support/gen_send_header.awk ../sphubd/sphashd_cmd.in > sphashd_client_send.h
awk -f ../support/gen_notification_source.awk notifications.in > notifications.c
awk -f ../support/gen_notification_header.awk notifications.in > notifications.h
compiling client.c
In file included from client.h:29,
                 from client.c:35:
hub.h:27:19: error: event.h: No such file or directory
In file included from client.h:29,
                 from client.c:35:
hub.h:85: error: field ‘idle_timeout_event’ has incomplete type
hub.h:89: error: field ‘reconnect_event’ has incomplete type
In file included from hub.h:123,
                 from client.h:29,
                 from client.c:35:
search_listener.h:71: error: field ‘in_event’ has incomplete type
In file included from client.h:30,
                 from client.c:35:
queue.h:32:35: error: db.h: No such file or directory
cc1: warnings being treated as errors
In file included from client.h:31,
                 from client.c:35:
../splib/io.h:46: warning: ‘struct evbuffer’ declared inside parameter list
../splib/io.h:46: warning: its scope is only this definition or declaration, which is probably not what you want
In file included from ui.h:27,
                 from client.h:32,
                 from client.c:35:
ui_cmd.h:16: error: field ‘send_state_event’ has incomplete type
In file included from client.c:35:
client.h:68: error: field ‘handshake_timer_event’ has incomplete type
client.c: In function ‘cc_send_string’:
client.c:158: warning: implicit declaration of function ‘bufferevent_write’
client.c: In function ‘cc_close_connection’:
client.c:215: warning: implicit declaration of function ‘bufferevent_free’
client.c:223: warning: implicit declaration of function ‘event_initialized’
client.c:225: warning: implicit declaration of function ‘event_del’
client.c: In function ‘cc_in_event’:
client.c:287: warning: implicit declaration of function ‘EVBUFFER_INPUT’
client.c:287: warning: passing argument 1 of ‘io_evbuffer_readline’ makes pointer from integer without a cast
client.c: In function ‘cc_add_channel’:
client.c:393: warning: implicit declaration of function ‘bufferevent_new’
client.c:393: warning: assignment makes pointer from integer without a cast
client.c:394: warning: implicit declaration of function ‘bufferevent_enable’
client.c:394: error: ‘EV_READ’ undeclared (first use in this function)
client.c:394: error: (Each undeclared identifier is reported only once
client.c:394: error: for each function it appears in.)
client.c:394: error: ‘EV_WRITE’ undeclared (first use in this function)
client.c:414: warning: implicit declaration of function ‘evtimer_set’
client.c:417: warning: implicit declaration of function ‘evtimer_add’
client.c: In function ‘cc_set_transfer_stats_interval’:
client.c:565: error: storage size of ‘ev’ isn’t known
client.c:570: warning: implicit declaration of function ‘evtimer_del’
client.c:565: warning: unused variable ‘ev’
command was: cc -c -o client.o client.c -I../bzip2-install/include -I../libiconv-install/include -I../libevent-install/include -I../expat-install/include -I../db-install/include -g -O2 -Wall -Werror -DVERSION="20061007" -DPACKAGE="shakespeer" -I../splib -I../spclient -D_FILE_OFFSET_BITS=64 -DCOREDUMPS_ENABLED=1 
make: *** [client.o] Error 1[/SIZE]After that I read some [articles]("http://shakespeer.bzero.se/forum/viewtopic.php?t=466&postdays=0&postorder=asc&highlight=tarball&start=0") on the shakespeer forum about compiling on linux. After reading it I executed the make command from the main directory. After a lot of text on the screen it ended with some errors.
I do now have a new file in the sphubd directory called sphubd but I can't execute it (also with sudo it doesn't work).

Any suggestions?

---

### Post by kson on 2006-10-26
Made a clean install myself and updated the first post. You are right about "make" in the sphubd directory but my binarys works after a make in the directory below.

---

### Post by ephesius on 2008-10-24
Sorry to dig up an old thread but has anyone successfully done this?

---

### Post by kson on 2008-11-02
> **ephesius said:**
> Sorry to dig up an old thread but has anyone successfully done this?

Yes definitly!

---

### Post by ephesius on 2008-11-02
Any chance you couldn't post a guide on how to do it? I keep getting make errors but im not sure what they're from...

---

### Post by kson on 2008-11-02
> **ephesius said:**
> Any chance you couldn't post a guide on how to do it? I keep getting make errors but im not sure what they're from...

No, sorry. I don't have it running anymore, I'm pure MacOSX nowadays. But I can tell you that it works. Have you tried the Shakespeer forum?

---

### Post by ephesius on 2008-12-17
Ok so I had a chance to try installing this again and everything seems to compile fine but then it errors at the end.

linking sphubd
../libevent-install/lib/libevent.a(event.o): In function `detect_monotonic':
event.c:(.text+0x12): undefined reference to `clock_gettime'
../libevent-install/lib/libevent.a(event.o): In function `gettime':
event.c:(.text+0x80): undefined reference to `clock_gettime'
../libevent-install/lib/libevent.a(evdns.o): In function `default_transaction_id_fn':
evdns.c:(.text+0x19c8): undefined reference to `clock_gettime'
evdns.c:(.text+0x19e6): undefined reference to `clock_gettime'
collect2: ld returned 1 exit status
command was: cc -o sphubd client.o client_cmd.o client_download.o client_upload.o hub.o hub_cmd.o hub_slots.o hub_list.o queue_db.o queue.o queue_match.o queue_directory.o queue_connect.o queue_auto_search.o search_listener.o sphubd.o user.o extip.o ui.o ui_cmd.o ui_send.o ui_list.o globals.o sphashd_client.o sphashd_client_cmd.o sphashd_client_send.o share.o share_save.o share_scan.o share_search.o share_tth.o share_bloom.o tthdb.o notifications.o extra_slots.o ../spclient/libspclient.a ../splib/libsplib.a  -L../spclient -lspclient -L../splib -lsplib    -lbz2  -lexpat  ../libevent-install/lib/libevent.a -lresolv
make[1]: *** [sphubd] Error 1
make[1]: Leaving directory `/home/user/shakespeer-read-only/sphubd'
make: *** [all] Error 1


Any ideas?

---

### Post by madpotato on 2009-02-13
ephesius,

Try installing libevent-dev from ubuntu repositories. In my case this fixed the error.

---

