---
title: "help with sorting in javascript?"
date: 2007-01-25
forum: The Cafe
---

### Post by sagarhshah on 2007-01-25
Hi I am doing a computing assignment in which I have been given some ready code and the data comes out in a raw format and I have to put it into a sortable manner i.e into a multidimensional array for later use.

an example of raw data is 
here=K;U;8.4:K;P;U;6.1:K;BA;BR;W;BO;U;29:K;BA;BR;W;BL;BO;U;20.1:K;BA;BL;W;BO;U;27.2:K;BA;BL;BO;U;16.1
another example is 
here=BR;W;BO;19.1:BR;W;BL;BO;10.2:BR;W;BL;BA;K;U;BO;22.7:BR;W;BL;BA;K;P;U;BO;20.4:BR;BA;K;U;BO;18.3:BR;BA;K;P;U;BO;16:BR;BA;BL;W;BO;25.3:BR;BA;BL;BO;14.2

the data has to be sorted into a multidimensional array. the split is : for each element of the array and the other split is ; for each element of an element of the array

here is whatI have so far
***********************************start code*******************************
function sortRoutes (route) {

	var data = route.split(':');
	for (i = 0; (i < data.length); i++) {
		data[i] = unescape(data[i]);
		}

		window.alert("first Data Sort Done"); //lets me know first bit of sort is done
  
// for (i = 0; (i < data.length); i++) {		//display the result of the first sort
// 	document.write("<p> available path no." + i + " = " + data[i] + "</p>");
//				}
	 
	 
	 for (x = 0; (x < data.length); x++) {
	 	for (y = 0; (y < ddata[x].length); y++) {
	 		var ddata = data[x].split(';');
	 		ddata[x][y] = unescape(ddata[x][y]); 
	     		}	
	}

}
***********************************end code********************************

I know the first sort works as I have checked it with various means to see the results. but the second sort is killing me. I can't get it to display after it has been sorted. am I doing something wrong here? all help will be appreciated.
Many Thanks in advance!!

Sagar

---

### Post by ember on 2007-01-25
Hi,

looking specifically at the second loop

```

for (x = 0; (x < data.length); x++) {
     for (y = 0; (y < ddata[x].length); y++) {
           var ddata = data[x].split(';');
            ddata[x][y] = unescape(ddata[x][y]);
     }
}

```

it seems to me that ddata[x].lenght is unknown when you try to enter the inner loop. Also I don't think you need to run through the array twice. Try:

```


function sortIt (encodedString)
{
  var data = encodedString.split(':');
  var result = array();
  
  for (i = 0; i < data.length; i++)
  {
     var subData = data[i].split(';');
     for (j = 0; j < subData.length; j++)
     {
       result[i][j] = subData[j];
     }
  }
}

```

I don't think you need to escape/unescape something here, but you could insert that function to your needs.

Also I like to recommend [FireBug]("http://www.getfirebug.com"), the latest and greatest Javascript, CSS and DOM-Debugging-Extension for Firefox which just was released as stable version 1.0.

Best wishes,
ember

---

### Post by JamieC on 2007-01-25
How's this:
```

<script type="text/javascript">
function sortRoutes (sRoute) {
    var aRoute      = unescape(sRoute).split(':');
    for (i in aRoute)
    {
        // document.write(unescape(aRoute[i]) + '<br />');

        var aSubRoute = unescape(aRoute[i]).split(';');
        for (j in aSubRoute)
        {
            // document.write('&nbsp;>' + unescape(aSubRoute[j]) + '<br />');
            aRoute[i][j] = unescape(aSubRoute[j]);
        }
    }
}

sortRoutes('BR;W;BO;19.1:BR;W;BL;BO;10.2:BR;W;BL;BA;K;U;B O;22.7:BR;W;BL;BA;K;P;U;BO;20.4:BR;BA;K;U;BO;18.3: BR;BA;K;P;U;BO;16:BR;BA;BL;W;BO;25.3:BR;BA;BL;BO;1 4.2');
</script>

```

Output (when uncommented):
> 
BR;W;BO;19.1
 >BR
 >W
 >BO
 >19.1
BR;W;BL;BO;10.2
 >BR
 >W
 >BL
 >BO
 >10.2
BR;W;BL;BA;K;U;B O;22.7
 >BR
 >W
 >BL
 >BA
 >K
 >U
 >B O
 >22.7
BR;W;BL;BA;K;P;U;BO;20.4
 >BR
 >W
 >BL
 >BA
 >K
 >P
 >U
 >BO
 >20.4
BR;BA;K;U;BO;18.3
 >BR
 >BA
 >K
 >U
 >BO
 >18.3
BR;BA;K;P;U;BO;16
 > BR
 >BA
 >K
 >P
 >U
 >BO
 >16
BR;BA;BL;W;BO;25.3
 >BR
 >BA
 >BL
 >W
 >BO
 >25.3
BR;BA;BL;BO;1 4.2
 >BR
 >BA
 >BL
 >BO
 >1 4.2


---

### Post by sagarhshah on 2007-01-26
Heya
JamieC

Your method seems to work when your printing tp screen it from  using the subRoute[j] , but after its been inserted into aRoute[i][j] is where the problem starts and I seem to be getting semi colons coming up when I try printing it to screen.

> function sortIt (sRoute) {
    var aRoute      = unescape(sRoute).split(':');
    for (i in aRoute)
    {
        document.write(unescape(aRoute[i]) + '<br />');

        var aSubRoute = unescape(aRoute[i]).split(';');
        for (j in aSubRoute)
        {
            
            aRoute[i][j] = aSubRoute[j];
            document.write('&nbsp;>' + unescape(aRoute[i][j]) + '<br />');
        }
    }
}

This is what I get

> BR;W;BO;19.1
 >B
 >R
 >;
 >W
BR;W;BL;BO;10.2
 >B
 >R
 >;
 >W
 >;
BR;W;BL;BA;K;U;BO;22.7
 >B
 >R
 >;
 >W
 >;
 >B
 >L
 >;
BR;W;BL;BA;K;P;U;BO;20.4
 >B
 >R
 >;
 >W
 >;
 >B
 >L
 >;
 >B
BR;BA;K;U;BO;18.3
 >B
 >R
 >;
 >B
 >A
 >;
BR;BA;K;P;U;BO;16
 >B
 >R
 >;
 >B
 >A
 >;
 >K
BR;BA;BL;W;BO;25.3
 >B
 >R
 >;
 >B
 >A
 >;
BR;BA;BL;BO;14.2
 >B
 >R
 >;
 >B
 >A

See what I mean about the semicolons? and also places where there supposed to be two characters like BR or BO they also seem to get separated into different lines.

Ember's method also seems to be similar with very few differences but giving me the same result.

Thanks for trying though. Guess I'll just have to keep on working on it till I get it working.

Sagar

---

