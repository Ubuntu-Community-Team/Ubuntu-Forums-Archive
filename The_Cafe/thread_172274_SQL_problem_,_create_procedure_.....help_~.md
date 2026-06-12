---
title: "SQL problem , create procedure .....help ~"
date: 2006-05-08
forum: The Cafe
---

### Post by 008325 on 2006-05-08
i pasted the following code to import the procedure , but i got the error


```

CREATE FUNCTION `nOrder`(pusr VARCHAR(16), pdate DATETIME) RETURNS int(11)
BEGIN

  DECLARE caddr VARCHAR(100);

  DECLARE pcid,poid INTEGER;



  SELECT C_No,C_Addr INTO pcid,caddr

  FROM customer

  WHERE C_Username = pusr;



  INSERT INTO orders(C_No,O_Date,O_Addr) VALUES (pcid,pdate,caddr);



  SELECT MAX(O_No) INTO poid FROM orders;

  RETURN poid;

END
```

```
#1064 - You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'VARCHAR(100)' at line 4 
```


any suggestion ? thx all

---

### Post by 008325 on 2006-05-08
push

---

### Post by Stormy Eyes on 2006-05-08
[MySQL doesn't implement INTEGER. Use INT instead, or one of the types listed in the linked manual page.](http://dev.mysql.com/doc/refman/5.0/en/numeric-types.html)

---

