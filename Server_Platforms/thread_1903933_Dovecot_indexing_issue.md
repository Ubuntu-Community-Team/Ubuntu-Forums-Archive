---
title: "Dovecot indexing issue"
date: 2012-01-03
forum: Server Platforms
---

### Post by mikerobinson on 2012-01-03
I have a mail folder with almost 36000 emails in it stored in Maildir format. When doing full body searches using my email client, it takes quite a while to do basic searches in message bodies and I would assume that the index is not being used. When telneting to my mail server, I try to do a search, but the connection quits on me after a few minutes and before the index is created.

> a2 EXAMINE INBOX
* FLAGS (\Answered \Flagged \Deleted \Seen \Draft Junk NonJunk $label1 $label5 $Forwarded $label2 $label3 $label4)
* OK [PERMANENTFLAGS ()] Read-only mailbox.
* 35941 EXISTS
* 0 RECENT
* OK [UNSEEN 35861] First unseen.
* OK [UIDVALIDITY 1264287638] UIDs valid
* OK [UIDNEXT 59985] Predicted next UID
* OK [HIGHESTMODSEQ 16] Highest
a2 OK [READ-ONLY] Select completed.
a2 SEARCH TEXT xyzzyx
* OK Indexed 2% of the mailbox, ETA 6:08
* OK Indexed 5% of the mailbox, ETA 5:28
* OK Indexed 8% of the mailbox, ETA 5:38
* OK Indexed 10% of the mailbox, ETA 5:25
* OK Indexed 13% of the mailbox, ETA 5:10
* OK Indexed 16% of the mailbox, ETA 5:00
* OK Indexed 19% of the mailbox, ETA 4:51
* OK Indexed 21% of the mailbox, ETA 4:47
* OK Indexed 24% of the mailbox, ETA 4:41
* OK Indexed 28% of the mailbox, ETA 4:13
* OK Indexed 30% of the mailbox, ETA 4:14
* OK Indexed 32% of the mailbox, ETA 4:07
* OK Indexed 34% of the mailbox, ETA 4:03
* OK Indexed 37% of the mailbox, ETA 3:56
* OK Indexed 39% of the mailbox, ETA 3:45
* OK Indexed 42% of the mailbox, ETA 3:37
* OK Indexed 44% of the mailbox, ETA 3:34
* OK Indexed 46% of the mailbox, ETA 3:25
* OK Indexed 48% of the mailbox, ETA 3:19
* OK Indexed 51% of the mailbox, ETA 3:10
* OK Indexed 53% of the mailbox, ETA 3:00
* OK Indexed 56% of the mailbox, ETA 2:51
Connection closed by foreign host.


I thought that maybe it would continue running in the background, but doing it again for a second time yields basically the same thing. I did it a few more times and the ETAs went down, but it quits every single time just before 50%:

> 
a2 SEARCH TEXT xyzzyx
* OK Indexed 6% of the mailbox, ETA 2:15
* OK Indexed 13% of the mailbox, ETA 2:07
* OK Indexed 19% of the mailbox, ETA 2:01
* OK Indexed 25% of the mailbox, ETA 1:54
* OK Indexed 30% of the mailbox, ETA 1:53
* OK Indexed 35% of the mailbox, ETA 1:46
* OK Indexed 41% of the mailbox, ETA 1:37
* OK Indexed 47% of the mailbox, ETA 1:29
Connection closed by foreign host.

Any ideas what's going on here?

Here's my configuration:

> $ sudo dovecot -n
# 1.2.15: /etc/dovecot/dovecot.conf
# OS: Linux 2.6.38-13-generic-pae i686 Ubuntu 11.04 
log_timestamp: %Y-%m-%d %H:%M:%S 
protocols: imap pop3 imaps pop3s managesieve
ssl_cert_file: /etc/ssl/certs/ssl-mail.pem
ssl_key_file: /etc/ssl/private/ssl-mail.key
ssl_cipher_list: ALL:!LOW:!SSLv2:ALL:!aNULL:!ADH:!eNULL:!EXP:RC4+RSA:+HIGH:+MEDIUM
login_dir: /var/run/dovecot/login
login_executable(default): /usr/lib/dovecot/imap-login
login_executable(imap): /usr/lib/dovecot/imap-login
login_executable(pop3): /usr/lib/dovecot/pop3-login
login_executable(managesieve): /usr/lib/dovecot/managesieve-login
mail_privileged_group: mail
mail_location: maildir:~/Maildir
mbox_write_locks: fcntl dotlock
mail_executable(default): /usr/lib/dovecot/imap
mail_executable(imap): /usr/lib/dovecot/imap
mail_executable(pop3): /usr/lib/dovecot/pop3
mail_executable(managesieve): /usr/lib/dovecot/managesieve
mail_plugins(default): fts fts_squat
mail_plugins(imap): fts fts_squat
mail_plugins(pop3): 
mail_plugins(managesieve): 
mail_plugin_dir(default): /usr/lib/dovecot/modules/imap
mail_plugin_dir(imap): /usr/lib/dovecot/modules/imap
mail_plugin_dir(pop3): /usr/lib/dovecot/modules/pop3
mail_plugin_dir(managesieve): /usr/lib/dovecot/modules/managesieve
imap_client_workarounds(default): outlook-idle delay-newmail
imap_client_workarounds(imap): outlook-idle delay-newmail
imap_client_workarounds(pop3): 
imap_client_workarounds(managesieve): 
pop3_client_workarounds(default): 
pop3_client_workarounds(imap): 
pop3_client_workarounds(pop3): outlook-no-nuls oe-ns-eoh
pop3_client_workarounds(managesieve): 
lda:
  postmaster_address: postmaster
  mail_plugins: sieve
  quota_full_tempfail: yes
  deliver_log_format: msgid=%m: %$
  rejection_reason: Your message to <%t> was automatically rejected:%n%r
auth default:
  mechanisms: plain login
  passdb:
    driver: pam
  userdb:
    driver: passwd
  socket:
    type: listen
    client:
      path: /var/spool/postfix/private/dovecot-auth
      mode: 432
      user: postfix
      group: postfix
plugin:
  fts: squat
  fts_squat: partial=4 full=10
  sieve: ~/.dovecot.sieve
  sieve_dir: ~/sieve

---

