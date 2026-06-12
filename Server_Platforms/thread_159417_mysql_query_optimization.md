---
title: "mysql query optimization"
date: 2006-04-12
forum: Server Platforms
---

### Post by jdonnell on 2006-04-12
Not sure if anyone here could help with this, but here goes anyway :)

I'm trying to optimize a mysql query that is running very slowly (40 secs). I'm using mysql 4.1.
The query is 
```
select * from word where id in (select synonym_id from synonyms where word_id = 38283);
```

If these queries are run seperately they are very fast (0 secs). For some reason when I put them together it isn't using the primary key for the outer query. Anyone have any ideas why or how to fix it?

```

mysql> explain select * from word where id in (38284, 38283);
+----+-------------+-------+-------+---------------+---------+---------+------+------+-------------+
| id | select_type | table | type  | possible_keys | key     | key_len | ref  | rows | Extra       |
+----+-------------+-------+-------+---------------+---------+---------+------+------+-------------+
| 1  | SIMPLE      | word  | range | PRIMARY       | PRIMARY | 4       |      | 2    | Using where |
+----+-------------+-------+-------+---------------+---------+---------+------+------+-------------+
1 row in set (0.30 sec)

mysql> explain select synonym_id from synonyms where word_id = 38283;
+----+-------------+----------+------+---------------+------+---------+------+------+-------------+
| id | select_type | table    | type | possible_keys | key  | key_len | ref  | rows | Extra       |
+----+-------------+----------+------+---------------+------+---------+------+------+-------------+
| 1  | SIMPLE      | synonyms | ALL  |               |      |         |      | 268  | Using where |
+----+-------------+----------+------+---------------+------+---------+------+------+-------------+
1 row in set (0.00 sec)

mysql> explain select * from word where id in (select synonym_id from synonyms where word_id = 38283);
+----+--------------------+----------+------+---------------+------+---------+------+------+-------------+
| id | select_type        | table    | type | possible_keys | key  | key_len | ref  | rows | Extra       |
+----+--------------------+----------+------+---------------+------+---------+------+------+-------------+
| 1  | PRIMARY            | word     | ALL  |               |      |         |      | 25   | Using where |
| 2  | DEPENDENT SUBQUERY | synonyms | ALL  |               |      |         |      | 268  | Using where |
+----+--------------------+----------+------+---------------+------+---------+------+------+-------------+
2 rows in set (0.00 sec)

```

---

### Post by nemequ on 2006-04-12
Not the right place for this. Try forums.mysql.com or lists.mysql.com.

---

### Post by jdonnell on 2006-04-12
thanks for the links

---

