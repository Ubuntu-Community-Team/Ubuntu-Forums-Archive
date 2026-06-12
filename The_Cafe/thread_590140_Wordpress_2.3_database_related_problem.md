---
title: "Wordpress 2.3 database related problem"
date: 2007-10-24
forum: The Cafe
---

### Post by Zelut on 2007-10-24
disclaimer: this question is not ubuntu related but since we've got the best and brightest minds here I thought I'd give it a try.  Also, yes I have googled this to no end and asked on the WP forums (which are crap in comparison).

I updated my blog to WP 2.3 last month, which I have regretted since.  I have database errors on all of my blogs and I can not figure out why.

An example error when I add a link to my blogroll:
> 
WordPress database error: [Duplicate entry '47' for key 1]
INSERT INTO wp_term_relationships (object_id, term_taxonomy_id) VALUES ('47', '21')

Warning: Cannot modify header information - headers already sent by (output started at /home/ubuntutu/public_html/wp-includes/wp-db.php:160) in /home/ubuntutu/public_html/wp-includes/pluggable.php on line 390

Yes, all plugins are deactivated.

I even tried a force upgrade again to maybe coax the database into submission.  I got this error and then it said it was done:
> 
WordPress database error: [Multiple primary key defined]
ALTER TABLE wp_term_relationships ADD PRIMARY KEY (object_id,term_taxonomy_id)

WordPress database error: [Table 'ubuntutu_wrdp1.wp_categories' doesn't exist]
SELECT * FROM wp_categories ORDER BY cat_ID

WordPress database error: [Table 'ubuntutu_wrdp1.wp_post2cat' doesn't exist]
SELECT * FROM wp_post2cat

WordPress database error: [Table 'ubuntutu_wrdp1.wp_link2cat' doesn't exist]
SELECT * FROM wp_link2cat

if anyone has any ideas on how I can fix this I would *really* appreciate it.

---

### Post by 505 on 2007-10-24
Try to run the following query:

SELECT object_id,COUNT(*) AS c FROM wp_term_relationships GROUP BY object_id ORDER BY c DESC

Haven't tested the query, but what it should produce is some object_id's with a value besides it. From the look of the error messages you have a table where more tuples have the same primary key. If you see any object_id's with a c-value higher than 1, it's not good. You then need to manually change one of the tuples to the next available object_id

Also, it seems that you don't have  a table called wp_categories, wp_post2cat, and wp_link2cat. I'd advice you to install phpMyAdmin and check that out. If the tables are indeed missing, find the structure of the tables somewhere, and create the tables again.

---

### Post by nixternal on 2007-10-24
> WordPress database error: [Table 'ubuntutu_wrdp1.wp_categories' doesn't exist]
 SELECT * FROM wp_categories ORDER BY cat_ID

fix in theme files -> s/categories/term
 
 > WordPress database error: [Table 'ubuntutu_wrdp1.wp_post2cat' doesn't exist]
 SELECT * FROM wp_post2cat

fix in theme files -> s/post2cat/post2term
 
> WordPress database error: [Table 'ubuntutu_wrdp1.wp_link2cat' doesn't exist]
 SELECT * FROM wp_link2cat

fix in theme files -> s/link2cat/link2term

---

