---
title: "Mailman isn't starting"
date: 2011-02-06
forum: Server Platforms
---

### Post by KeepXtreme on 2011-02-06
Hi folks, we got following problem on our Squeeze-Server - quoted from the mailman-logs:
qrunner-log:
> Master qrunner detected subprocess quit (this messages appears for several subprocesses)

and later:
> Qrunner xy reached maximum restart limit of 10, not restarting


error-log:
(translated)
> No subprocess with PID xxxxx available
[Erno 3] No such process

these messages for ever restart-try of Mailman


what you also have to know:
-we had some Problems with exim4 on Friday (stopt delivering mails). We corrected the wrong configurationfiles and exim delivers mails know as he should
-on Saturday I recieved a message, that mailman still delivers mails only emails existing on the server. funny was, that the emails are sent via an extern smtp-Server and returning to the sever later (example@fmc.uni-karlsruhe.de - but the server name is different) so there shouldn't be any difference between the mail-adresses. Ok, taught, the other admin forgot to restart mailman the day before after he corrected exim (but he had restarted mailman succesfully as I know now) an so I tried ```
/etc/init.d/mailman restart
```
-after this point, mailman doesn't start anymore
-the webinterface telling something:
> Bug in Mailman version <undetermined>

We're sorry, we hit a bug!

Please inform the webmaster for this site of this problem. Printing of traceback and other system information has been explicitly inhibited, but the webmaster can find this information in the Mailman error logs.



can somebody help? its realy urgend to get mailman back to work...
the reason, why I wrting in this forum is just <ou guys solved some of my previos problems and in the debian-forums nobody anwers my question - not even tried :( 


PS:
check_db ->notething to do
check_perms -> all fine



edit:// ok, a forced Reinstallation of Mailman&Python solved the problem - whyever...

---

