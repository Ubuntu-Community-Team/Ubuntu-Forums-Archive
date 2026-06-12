---
title: "What is XML ingestion?"
date: 2008-11-23
forum: The Cafe
---

### Post by Xarok on 2008-11-23
Sorry not Ubuntu related... ( I just like asking you guys 'cause you're leet)

But does anyone know what XML ingestion is?

Can't seem to find anything about it on the nets.

Thanks!!

---

### Post by -grubby on 2008-11-23
I don't think XML is part of a healthy diet.

---

### Post by Trail on 2008-11-24
Well, I haven't met the term before, but I'd guess it's similar to SQL injection.
Imagine you are a server, you receive text from users, store that text on XML files and then execute some actions on those files. You could have something like that:

```

<?xml.....>
<body>
  <user>
     <requestText>...</requestText>
     <language>...</language>
     <remainingCredit>...</remainingCredit>
  </user>
</body>

```

The user then can input his data through a web form, and it will be stored in the XML. So if he types "blahblah" as a requestText in the webform, the XML might look like this:

```

<?xml.....>
<body>
  <user>
     <requestText>blahblah</requestText>
     <language>en</language>
     <remainingCredit>50</remainingCredit>
  </user>
</body>

```

Which is ok. But what about if the user enters the following text in the webform?
```

blahblah</requestText><language>en</language><remainingCredit>500000</remainingCredit></user></body>

```

The end result would look like this:
```

<?xml.....>
<body>
  <user>
     <requestText>blahblah</requestText>
     <language>en</language>
     <remainingCredit>500000</remainingCredit>
  </user>
</body>
</requestText>
<language>en</language>
<remainingCredit>50</remainingCredit>
</user>
</body>

```

So he just got himself stored with 500000 credits. Fraud.

The solution to the SQL injection problem was to escape the "<",">", etc symbols with &gt, &lt and the like. I guess preventing XML injecting would be similar.

---

### Post by jespdj on 2008-11-24
Ingesting XML is not a good idea, all those pointy brackets will get stuck in your throat. :lolflag:

If you want a serious answer: Can you give some context where you read this?

---

### Post by Trail on 2008-11-24
Actually, i just realised it's not about inje**c**tion. Yay me.

Bah.

---

