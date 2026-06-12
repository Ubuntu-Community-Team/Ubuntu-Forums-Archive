---
title: "is unicode my problem?"
date: 2010-04-03
forum: The Cafe
---

### Post by chris200x9 on 2010-04-03
I have started to write an ebarassingly easy function but it won't work. I have checked numorus tutorials and it should work, then I found some mention of it being for ASCII. So my question is, is there something wrong with this code or is it because geany uses unicode?

```
 string FixSentence( string sentance)
{
	int i = 0;
	string newstring;
	while (sentance[i])
	{
		newstring[i] =  tolower(sentance[i]);
		
	i++;
	}
	cout << newstring;
	return "";
} 
```

---

### Post by chris200x9 on 2010-04-03
can somebody close this. Sorry

---

### Post by cariboo on 2010-04-04
Closed by request.

---

