---
title: "PHP/MYSQL order by date"
date: 2009-04-29
forum: Server Platforms
---

### Post by Black Mage on 2009-04-29
Hey, I am working on a forum and I'm trying to order the forums by when it has been most recently updated.

My tables look like

topic_list(topicid,topic, date_created, is_deleted)

post_data(topicid, postid, post, date_created, date_modified, userid)

So I have:

SELECT DISTINCT topic_list.topicid, topic_list.date created FROM topic_list
JOIN post_data ON post_data.topicid=topic_list.topic_id
WHERE topicid=$value
ORDER BY post_data.date_modified DESC

And it doesn't seem to work and give the highest values. I can't figure out what order it is giving the vales in. The problem seems to come in when I use DISTINCT, but I can't figure out why that would cause a problem.
Any help would be greatly appreciated.

---

### Post by kamaji792 on 2009-04-30
I am a long way from an expert on this but:

Don't you have to 'SELECT' 'post_data.date_modified' so you can the order the results by it?

All the best

---

