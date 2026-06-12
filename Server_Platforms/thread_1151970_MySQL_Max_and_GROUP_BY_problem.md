---
title: "MySQL Max and GROUP BY problem"
date: 2009-05-07
forum: Server Platforms
---

### Post by Black Mage on 2009-05-07
Hey,

I'm having a problem with MYSQL, trying to get stuff to order correctly. I have a table that looks like this:

message_table(thread_id, message_id, sender_id, date_sent, subject, message)

<table>
<tr>
<td>thread_id</td>
<td>message_id</td>
<td>sender_id</td>
<td>date_sent</td>
<td>subject</td>
<td>message</td>
</tr>
<tr>
<td>1</td>
<td>1</td>
<td>1</td>
<td>May 1, 2008</td>
<td>Mesage 1</td>
<td>dsfsf</td>
</tr>
<tr>
<td>2</td>
<td>1</td>
<td>2</td>
<td>May 2, 2008</td>
<td>Mesage 2</td>
<td>sff</td>
</tr>
<tr>
<td>1</td>
<td>2</td>
<td>2</td>
<td>May 3, 2008</td>
<td>Mesage 1</td>
<td>sdf</td>
</tr>
<tr>
<td>2</td>
<td>2</td>
<td>1</td>
<td>May 4, 2008</td>
<td>Mesage 2</td>
<td>sf</td>
</tr>
</table>

I try by grouping and ordering to get the most recent message but it doesn't work. My SQL looks like this:

SELECT thread_id, MAX( date_sent ) , message
FROM messanging_table
GROUP BY thread_id

It gets the date correctly everything else is wrong. What am I doing wrong with my SQL?

---

