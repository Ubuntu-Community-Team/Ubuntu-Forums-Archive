---
title: "ossec hids include unwanted info in alert message"
date: 2010-10-01
forum: Security
---

### Post by vaccinus on 2010-10-01
Hello!
Can someone help me with advice

A have ossec server installed & couple of ossec agents. Server sends alert messages with email_alert_level 9.

Sometimes in messages are included alerts from other hosts with alert level 2 (ok with level ,rule id="1002" have option alert_by_email). But is there a way to exclude those level 2 alerts from from messages like: "OSSEC Notification - (myhost.exapmle) 10.10.10.10 - Alert level 9"?

'Couse sometimes alert messages is hard to read, if there are a lots of them :( Yea, I know, these alerts should be examined & fixed.. :)

Thanks in advance :)

---

### Post by bodhi.zazen on 2010-10-01
personally, with ossec, I disable email alerts and monitor ossec via the web interface.

---

### Post by vaccinus on 2010-10-02
> **bodhi.zazen said:**
> personally, with ossec, I disable email alerts and monitor ossec via the web interface.

Ou, if this is only thing to do... or it's not real time anymore. & I like to get SMS about 10+ events :)

---

