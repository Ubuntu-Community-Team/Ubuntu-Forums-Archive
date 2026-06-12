---
title: "exim4 router condition"
date: 2010-08-18
forum: Server Platforms
---

### Post by BarreSwe on 2010-08-18
Hi, 
I'm trying to create a condition for one och my routers in exim4.
The condition should consist of two parts and both should be "true".

the first working condition is a lookup in mysql, and this works:
```
condition = ${lookup mysql{ \                                                                                              
                   SELECT email FROM users \                                                                                    
                   WHERE email='${quote_mysql:$local_part}@${quote_mysql:$domain}'} \ 
                   {true}{false}}

```The second condition is a string comparison in the subject-field, this also works:
```
condition = ${if match {$h_subject:}{\N^kallekalas$\N}{yes}{no}}
```No matter what I do when i combine those into a single condition it fails.

this is my latest try (just before I almost threw exim4 out, cus I can't understand the syntax :)), it's not working. Maybe some poor soul can help me understand what I'm doing wrong.

```
   condition = ${if and { \
                   {lookup mysql{ \                                                  
                     SELECT email FROM users \                                       
                     WHERE email='${quote_mysql:$local_part}@${quote_mysql:$domain}'} \ 
                     {true}{false} \
                   } \
                   {match {$h_subject:}{\N^kallekalas$\N}{true}{false}} \
                  }}

```Thanks in advance

---

