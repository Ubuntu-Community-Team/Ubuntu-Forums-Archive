---
title: "[SOLVED] Fetchmail Hangs after successfully logging into POP3 Server"
date: 2007-12-07
forum: Server Platforms
---

### Post by charmcity on 2007-12-07
Hi,

I'm experiencing Fetchmail hanging after it successfully logs into a POP3 account I'm trying to poll.  If anyone can help - I'd appreciate it:

Fetchmail -V output:
```
genesis@tommy:~$ fetchmail -v
fetchmail: 6.3.8 querying mail.genesismidatlantic.com (protocol POP3) at Fri 07 Dec 2007 09:14:05 PM EST: poll started
fetchmail: Trying to connect to 66.153.17.74/110...connected.
fetchmail: POP3< +OK Microsoft Exchange 2000 POP3 server version 6.0.6603.0 (server.Genesis.local) ready.
fetchmail: POP3> CAPA
fetchmail: POP3< +OK Capability list follows
fetchmail: POP3< TOP
fetchmail: POP3< USER
fetchmail: POP3< PIPELINING
fetchmail: POP3< EXPIRE NEVER
fetchmail: POP3< UIDL
fetchmail: POP3< SASL NTLM
fetchmail: POP3< .
fetchmail: mail.genesismidatlantic.com: opportunistic upgrade to TLS failed, trying to continue.
fetchmail: POP3> USER tom
fetchmail: POP3< +OK
fetchmail: POP3> PASS *
fetchmail: POP3< +OK User successfully logged on.
fetchmail: POP3> STAT
fetchmail: POP3< +OK 4 30685
fetchmail: POP3> LAST
fetchmail: POP3< -ERR Protocol error.
fetchmail: Protocol error.
fetchmail: POP3> UIDL
fetchmail: POP3< +OK
fetchmail: POP3< 1 AAADadKAAAQz+HlExtz3sqU2uoxlY1qf
fetchmail: POP3< 2 AAQDadKAAAQz+HlExtz3sqU2uoxlY1qf
fetchmail: POP3< 3 AAgDadKAAAQz+HlExtz3sqU2uoxlY1qf
fetchmail: POP3< 4 AAAEadKAAAQz+HlExtz3sqU2uoxlY1qf
fetchmail: POP3< .
fetchmail: 4 messages for tom at mail.genesismidatlantic.com (30685 octets).
fetchmail: POP3> LIST 1
fetchmail: POP3< +OK 1 12836
fetchmail: POP3> TOP 1 99999999

```

Thats where it Hangs ---?  Then it will eventually time out after 300 seconds.

Can anyone tell me what could be going on?  Here is my .fetchmailrc

```
set logfile "/home/genesis/.fetchmail.log"

poll mail.genesismidatlantic.com proto pop3:
user "tom", with password "*****", is "genesis" here;

```

Thanks for your replies  ---
Tom

---

### Post by charmcity on 2007-12-09
I'm getting into the habit of replying to my own posts -- apologies.  I just thought you might be interested in the solution.

The Key to the problem was after retrying a few times I was really hanging on a "temporary failure" to identify the user account the mail messages are destined to go to -- a postfix problem  Which was strange considering everything had been working.

Upon close examination I was missing 2 lines to my main.cf file which solved the problem.  I added:

alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases

Which, would affect looking up users no?  So problem solved, just thought I'd share and thanks for reading!!

Cheers
Tom

---

