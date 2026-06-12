---
title: "Plymouth"
date: 2013-08-17
forum: Ubuntu Application Development
---

### Post by StalkerQF on 2013-08-17
Hello!

I want to create my splash-theme for plymouth daemon. I try to write plymouth script, but he doesn't work. Can you halp me with it?

```
# This is a simple testing script for Plymouth daemon.

Window.SetBackgroundTopColor (0.16, 0.00, 0.12);    
Window.SetBackgroundBottomColor (0.16, 0.00, 0.12);  
logo.image = Image ("ubuntu_logo16.png"); //&#1074;&#1099;&#1073;&#1080;&#1088;&#1072;&#1077;&#1084; &#1080;&#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1080;&#1077; &#1083;&#1086;&#1075;&#1086;&#1090;&#1080;&#1087;&#1072;


logo.sprite = Sprite (); //&#1089;&#1086;&#1079;&#1076;&#1072;&#1077;&#1084; &#1085;&#1086;&#1074;&#1099;&#1081; &#1089;&#1087;&#1088;&#1072;&#1081;&#1090;
logo.sprite.SetImage (logo.image);


logo.width = logo.image.GetWidth ();
logo.height = logo.image.GetHeight ();
logo.x = Window.GetX () + Window.GetWidth () / 2 - logo.width  / 2; 
logo.y = Window.GetY () + Window.GetHeight () / 2 - logo.height;
logo.z = 1000; 


logo.sprite.SetX (logo.x); //&#1079;&#1072;&#1076;&#1072;&#1105;&#1084; &#1082;&#1086;&#1086;&#1088;&#1076;&#1080;&#1085;&#1072;&#1090;&#1099; &#1083;&#1086;&#1075;&#1086;&#1090;&#1080;&#1087;&#1072;
logo.sprite.SetY (logo.y);
logo.sprite.SetZ (logo.z);


logo.sprite.SetOpacity (1);




light.image = Image ("light.png");


light.sprit = Sprite (light.image);


light.width = light.image.GetWidth ();
light.height = light.image.GetHeight ();
llight.x = Window.GetX () + Window.GetWidth () / 2 - llight.width  / 2; 
light.y = Window.GetY () + Window.GetHeight () / 2 - light.height;
light.z = 100; 


light.sprite.SetX (light.x);
light.sprite.SetY (light.y);
light.sprite.SetZ (light.z);


#light.sprite.SetOpacity (1);


fun pulse ()
 {
  int flag;
  float counter;
  if (flag = 0)
	{if (counter < 1)
		{
		counter = counter + 0.02;
		light.sprite.SetOpacity (counter);
		}
		else
		flag = 1;
	}	
	else
	{if (counter > 0)
		{		
		counter = counter - 0.02;
		light.sprite.SetOpacity (counter);
		}
		else
		flag = 0;
	}
 }


Plymouth.SetRefreshFunction (pulse);
```

Thanks.

---

