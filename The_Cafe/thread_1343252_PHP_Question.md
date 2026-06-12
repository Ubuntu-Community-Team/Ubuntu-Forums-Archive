---
title: "PHP Question"
date: 2009-12-01
forum: The Cafe
---

### Post by Gias Kay on 2009-12-01
What do the -> and => operations mean respectively? It's impossible to google related information so I have to ask it... Thank you very much.

---

### Post by jpmelos on 2009-12-01
The -> (arrow operator) uses a member of an object, when you are referencing that object. For exemplo, if you have an object called "bus" from the class "Autos", and you want to use the member "drive()", you use bus->drive().

I'm not 100% sure, but that's how it works in C++, and I know some PHP to guess it must be like that.

I don't know the => operator.

---

### Post by brian183 on 2009-12-01
=>
is the assignment operator for arrays to assign a value to a index.
[PHP]
$example = array(
	'index'	=> 'value'
);
[/PHP]

---

