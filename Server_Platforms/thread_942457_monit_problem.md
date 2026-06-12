---
title: "monit problem"
date: 2008-10-09
forum: Server Platforms
---

### Post by mitjab on 2008-10-09
sudo monit -t
i get
/etc/monit/monitrc:20: Error: syntax error 'From: monit@$HOST'

This is line 20

From: monit@$HOST # sender
Subject: monit alert -- $EVENT $SERVICE # subject

$EVENT Service $SERVICE

Date: $DATE
Action: $ACTION
Host: $HOST # body
Description: $DESCRIPTION

Your faithful,
monit

What is wrong here?

---

### Post by windependence on 2008-10-09
Do you have the variables defined somewhere? For example $HOST, $EVENT, $SERVICE, etc.

-Tim

---

