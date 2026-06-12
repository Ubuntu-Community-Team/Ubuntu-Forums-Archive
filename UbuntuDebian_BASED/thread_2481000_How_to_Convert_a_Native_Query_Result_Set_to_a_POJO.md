---
title: "How to Convert a Native Query Result Set to a POJO Class Collection Using JPA"
date: 2022-11-16
forum: Ubuntu/Debian BASED
---

### Post by ronakmehta on 2022-11-16
JPA is being used in my project.
I came across a query that required me to do a join operation on five tables. As a result, I wrote a native query that returns five fields.
Now I'd want to transform the result object to a java POJO class containing the same five Strings. Is there a method in JPA to cast that result directly to a POJO object list?
After reading this [tutorial]("https://www.scaler.com/topics/pojo-class-in-java/"), I came up with the following solution.

```
[COLOR=var(--highlight-keyword)][FONT=inherit]@NamedNativeQueries({  [/FONT][/COLOR]
[COLOR=var(--highlight-keyword)][FONT=inherit]    @NamedNativeQuery(  
        name = "nativeSQL",  
        query = "SELECT * FROM Actors",  
        resultClass = db.Actor.class),  
    @NamedNativeQuery(  
        name = "nativeSQL2",  
        query = "SELECT COUNT(*) FROM Actors",  
        resultClass = XXXXX) // <--------------- problem   [/FONT][/COLOR][COLOR=var(--highlight-keyword)][FONT=inherit]})[/FONT][/COLOR][COLOR=var(--highlight-color)][FONT=inherit] [/FONT][/COLOR]
```

Is it necessary to give a class that is a real JPA object in resultClass? OR can we convert it to any JAVA POJO class that has the same column names?

---

### Post by TheFu on 2022-11-16
Java questions really belong in the Programming sub-forum.  Probably 99% of the people in these forums don't know Java and even fewer will know "JPA", whatever that is.

You'll get more and better answers from a Java-specific forum. Hopefully, you aren't seeking a Java expert to respond here.

Figured you'd like to know that someone saw the post, even if I'm not actually helpful.

---

