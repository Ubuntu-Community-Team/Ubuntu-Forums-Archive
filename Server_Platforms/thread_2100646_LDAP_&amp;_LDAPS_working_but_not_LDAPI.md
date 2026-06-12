---
title: "LDAP &amp; LDAPS working but not LDAPI?"
date: 2013-01-02
forum: Server Platforms
---

### Post by Philip Colmer on 2013-01-02
I'm struggling to get LDAP with StartTLS (LDAPI) working even though I can get LDAPS working.

Running ldapsearch -x -H ldapi://<host> -d-1 gives me this output:

ldap_url_parse_ext(ldapi://<host>)
ldap_create
ldap_url_parse_ext(ldapi://<host>/??base)
ldap_sasl_bind
ldap_send_initial_request
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_path
ldap_new_socket: 3
ldap_connect_to_path: Trying <host>
ldap_connect_timeout: fd: 3 tm: -1 async: 0
ldap_ndelay_on: 3
ldap_close_socket: 3
ldap_err2string
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)

The LDAP server has been configured with a self-signed certificate and this seems to work with LDAPS so I don't *think* I have a certificate issue.

ldapsearch does work with ldap://, and it was my understanding that ldapi:// is LDAP + StartTLS so I don't understand why the connection doesn't work. I've tried running slapd in debug mode on the server and it doesn't seem to even see an incoming attempt at a connection.

What have I misunderstood or overlooked?

Thanks.

Philip

---

### Post by ranger12 on 2013-01-02
Are you running a firewall? If so I wonder if it is an issue of the necessary port not being open for incoming traffic. I have run into that on several occasions when I was setting up my server last summer. Just a thought.

---

### Post by Philip Colmer on 2013-01-03
> **ranger12 said:**
> Are you running a firewall? If so I wonder if it is an issue of the necessary port not being open for incoming traffic. I have run into that on several occasions when I was setting up my server last summer. Just a thought.

Well, it turns out I was in complete newbie mode :-(. LDAPI is *not* LDAP with TLS and I'm completely embarrassed to think it was.

I'm not actually bothered about LDAPI, but I *am* bothered about getting LDAP with TLS working ... I don't think it is because a tcpdump of the traffic shows the data in cleartext.

---

### Post by Philip Colmer on 2013-01-03
> **Philip Colmer said:**
> I *am* bothered about getting LDAP with TLS working ... I don't think it is because a tcpdump of the traffic shows the data in cleartext.

It looks like TLS is working after all. Thread marked as solved.

---

### Post by ranger12 on 2013-01-03
Well that s good, I actually don't have ldap setup with tls - just ldap.

---

