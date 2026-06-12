---
title: "[SOLVED] javascript question/issue?"
date: 2008-08-29
forum: The Cafe
---

### Post by moore.bryan on 2008-08-29
no matter what i do, i can't seem to get [this]("http://www.uky.edu/StudentOrgs/TSA/dhtmlExpandable.htm") menu setup. i've altered the htm, but still can't get it to work properly; in fact, a little strangely, clicking on the second item opens the other submenu... huh?
[here's]("http://www.bmoore.net/courses.htm") the webpage and [here's]("http://www.bmoore.net/scripts/menuExpandable.js") the script file. also, [this]("http://www.bmoore.net/css/menuExpandable.css") is the accompanying css. hope i'm just blind and can't see the issue.

thanks, in-advance, for anyone's help!

---

### Post by gjoellee on 2008-08-29
> **moore.bryan said:**
> no matter what i do, i can't seem to get [this]("http://www.uky.edu/StudentOrgs/TSA/dhtmlExpandable.htm") menu setup. i've altered the htm, but still can't get it to work properly; in fact, a little strangely, clicking on the second item opens the other submenu... huh?
[here's]("http://www.bmoore.net/courses.htm") the webpage and [here's]("http://www.bmoore.net/scripts/menuExpandable.js") the script file. also, [this]("http://www.bmoore.net/css/menuExpandable.css") is the accompanying css. hope i'm just blind and can't see the issue.

thanks, in-advance, for anyone's help!

Here is the websites source....
```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
    <meta name="GENERATOR" content="Microsoft FrontPage 5.0">
    <meta name="ProgId" content="FrontPage.Editor.Document">
    <title>Expandable List Menu Example, using DHTML</title>
    
    <meta http-equiv="Content-Type" content="text/html; charset=iso-8859-2" />

    <link rel="stylesheet" type="text/css" media="screen"
        href="global.css" />
        
    <link rel="stylesheet" type="text/css" media="screen" 
        href="menuExpandable.css" />    

    <script type="text/javascript" src="menuExpandable.js"></script>
    <script language="JavaScript">
       function greet(){
          alert("Hello user!");
       }
    </script>
    
    <base target="_self">
    
</head>
<body bgcolor="#EEEEEE">




<div id="menuDiv"><ul id="menuList">


        <li class="menubar">
    <a href="#" id="FileActuator" class="actuator">Grocery Store</a>
        <ul id="FileMenu" class="menu">

             <li><a href="seoul.htm" title="SSM" target="displaypage" onclick="greet()">Seoul Super Market</a></li>
              <li><a href="JPFINC.htm" title="JPFINC" target="displaypage">Japanese Foods, INC</a></li>
              <li><a href="YUYU.htm" title="YUYU" target="displaypage">Yu YU Asian Supermarket</a></li>
              <li><a href="HK.htm" title="HK" target="displaypage">Hong Kong Market</a></li>
          </ul>
      </li>
<!--
<li>
    <a href="#" id="NewActuator" class="actuator">New</a>
        <ul id="NewMenu" class="submenu">

    <li><a href="NewCase.jsp" title="Case">Case</a></li>
    <li><a href="index.jsp" title="Item">Item</a></li>
    <li><a href="index.jsp" title="Party">Party</a></li>
        </ul>
    </li>

<li>
    <a href="#" id="OpenActuator" class="actuator">Open</a>
        <ul id="OpenMenu" class="submenu">

    <li><a href="index.jsp" title="Case">Case</a></li>
    <li><a href="index.jsp" title="Item">Item</a></li>
    <li><a href="index.jsp" title="Party">Party</a></li>
        </ul>
    </li>

    <li><a href="index.jsp" title="Exit">Exit</a></li>
</ul>
-->
    


        <li class="menubar">

    <a href="#" id="EditActuator" class="actuator">Restaurant</a>
        <ul id="EditMenu" class="menu">

    <li><a href="tolly.htm" title="Tolly Ho" target="displaypage">Tolly Ho</a></li>
    <li><a href="applebee.htm" title="Applebee" target="displaypage">Applebee</a></li>
    <li><a href="hunan.htm" title="hunan" target="displaypage">Imperial Hunan</a></li>
    <li><a href="planetthai.htm" title="planetthai" target="displaypage">Planet Thai</a></li>
    <li><a href="http://www.pacificmooncafe.com/" title="pacificmoon" target="displaypage">Pacific Moon</a></li>
    <li><a href="tachibana.htm" title="Tachibana" target="displaypage">Tachibana</a></li>
    <li><a href="jade.htm" title="Jade Palace" target="displaypage">Jade Palace</a></li>
    
</ul>
    </li>


        <li class="menubar">

    <a href="#" id="CaseActuator" class="actuator">Shopping</a>
        <ul id="CaseMenu" class="menu">

<li>
    <a href="#" id="AddActuator" class="actuator">Computers</a>
        <ul id="AddMenu" class="submenu">

    <li><a href="http://www.pricewatch.com/" title="Pricewatch" target="displaypage">Pricewatch.com</a></li>
    <li><a href="http://www.newegg.com/" title="Newegg" target="displaypage">Newegg</a></li>
    <li><a href="http://stores.uky.edu" title="UK computer store" target="displaypage">UK computer store</a></li>
    <li><a href="http://www.techbargains.com/" title="Techbargains" target="displaypage">Techbargains</a></li>
    <li><a href="http://www.slickdeals.net/" title="Slickdeals" target="displaypage">Slickdeal</a></li>
    <li><a href="http://www.consumerreview.com/" title="Consumer Review" target="displaypage">Consumer Review</a></li>

        </ul>
    </li>

<li>
    <a href="#" id="Open71Actuator" class="actuator">Books</a>
        <ul id="Open71Menu" class="submenu">

    <li><a href="http://www.ukbookstore.com" title="UKbook" target="displaypage">UK Book store</a></li>
    <li><a href="http://www.kennedys.com" title="Kennedy" target="displaypage">Kennedy Book store</a></li>
    <li><a href="http://www.wildcattext.com/" title="wildcat" target="displaypage">Wildcat Book store</a></li>
    <li><a href="http://www.ecampus.com/" title="ecampus" target="displaypage">Ecampus</a></li>
    <li><a href="http://www.half.com" title="half" target="displaypage">Half.com</a></li>
        </ul

<link rel="stylesheet" type="text/css" media="screen"href="menuExpandable.css" />    

<script type="text/javascript" src="menuExpandable.js"></script>



make sure that the names, and paths are correct!>
    </li>
    
    <li>
    <a href="#" id="airActuator" class="actuator">Travel</a>
        <ul id="airMenu" class="submenu">

    <li><a href="happytour.htm" title="happytour" target="displaypage">Happy Tour</a></li>
    <li><a href="gateway.htm" title="gateway" target="displaypage">Gateway Travel</a></li>
    <li><a href="http://www.expedia.com/" title="expedia" target="displaypage">Expedia</a></li>
    <li><a href="http://www.site59.com/" title="site59" target="displaypage">Site59</a></li>
    <li><a href="http://www.orbitz.com" title="orbitz" target="displaypage">Orbitz</a></li>
    <li><a href="http://www.travelocity.com" title="travelocity" target="displaypage">Travelocity</a></li>
    <li><a href="http://www.roomsaver.com/" title="Traveler Discount Guide" target="displaypage">Traveler Discount Guide</a></li>
    <li><a href="http://www.frommers.com/" title="Frommers.com" target="displaypage">Frommers.com</a></li>
    <li><a href="http://www.fodors.com/" title="Fodors.com" target="displaypage">Fodors.com</a></li>
    <li><a href="http://www.flytecomm.com" title="Flytecomm.com" target="displaypage">FlyteComm.com</a></li>
        </ul>
    </li>

    <li>
    <a href="#" id="otherActuator" class="actuator">Others</a>
        <ul id="otherMenu" class="submenu">
     <li><a href="http://www.overstock.com" title="overstock" target="displaypage">Overstock.com</a></li>
     <li><a href="http://www.pricegrabber.com/" title="pricegrabber" target="displaypage">Pricegrabber.com</a></li>
     <li><a href="http://www.surprise.com/" title="surprise.com" target="displaypage">Surprise.com</a></li>
      <li><a href="h

<link rel="stylesheet" type="text/css" media="screen"href="menuExpandable.css" />    

<script type="text/javascript" src="menuExpandable.js"></script>



make sure that the names, and paths are correct!ttp://www.creditcardgoodies.com/" title="creditcom" target="displaypage">Credit Card Goodies</a></li>



     </ul>
    </li>


</ul>
    </li>
      
<li class="menubar">

    <a href="#" id="enterActuator" class="actuator">Entertainment</a>
        <ul id="enterMenu" class="menu">

    <li><a href="http://www.thestadiumllc.com/home.htm" title="stadium" target="displaypage">The Stadium</a></li>
    <li><a href="http://www.ebaumsworld.com/" title="ebaum" target="displaypage">ebaum</a></li>
    <li><a href="http://atomfilms.shockwave.com/af/home/" title="atom" target="displaypage">AtomFilms</a></li>
    <li><a href="http://jpmp3.com/" title="kyo" target="displaypage">Kyo Music</a></li>
    <li><a href="http://www.51hear.com/" title="51" target="displaypage">51 Hears</a></li>
    <li><a href="http://www.yesasia.com" title="yesasia" target="new">YesAsia</a></li>
    <li><a href="http://www.howstuffworks.com" title="howstuffwork" target="displaypage">How stuff works</a></li>
    <li><a href="http://www.dailycandy.com" title="dailycandy" target="displaypage">Daily Candy</a></li>
</ul>
    </li>

      <li class="menubar">
<a href="#" id="resourceActuator" class="actuator">Resources</a>
        <ul id="resourceMenu" class="menu">
<li>
    <a href="#" id="jobActuator" class="actuator">Job Search</a>
        <ul id="jobMenu" class="submenu">

    <li><a href="http://www.uky.edu/HR/studentjobs/welcome.php" title="UKHR" target="displaypage">UK Human Resources</a></li>
    <li><a href="http://www.uky.edu/CareerCenter/" title="CareerCenter" target="displaypage">UK Career Center</a></li>
    <li><a href="http://flipdog.monster.com/" title="flipdog" target="displaypage">Flipdog.com</a></li>
    <li><a href="http://www.careerbuilder.com/" title="careerbuilder" target="new">Career Builder</a></li>
    <li><a href="http://www.collegegrad.com/" title="collegegrade" target="new">CollegeGrad.com</a></li>
        </ul>
    </li>
    
     <li>
    <a href="#" id="searActuator" class="actuator">Search and reference</a>
        <ul id="searMenu" class="submenu">
     <li><a href="http://www.about.com" title="about" target="displaypage">About.com</a></li>
     <li><a href="http://www.dictionary.com" title="dicrionary" target="displaypage">Dictionary.com</a></li>
     <li><a href="http://www.webmd.com" title="webmd" target="displaypage">WebMD.com</a></li>
     <li><a href="http://www.broadbandreports.com" title="broadband" target="displaypage">Broadbandreports.com</a></li>
     <li><a href="http://www.internettrafficreport.com" title="internet" target="displaypage">Internet Traffic Report.com</a></li>
 
     </ul>
    </li>

      <li>
    <a href="#" id="orgsActuator" class="actuator">Orgs in TW</a>
        <ul id="orgsMenu" class="submenu">
     <li><a href="http://www.tcdms.taipei.gov.tw/" title="tcdms" target="displaypage">&#33274;&#21271;&#24066;&#20853;&#24441;&#34389;</a></li>
     <li><a href="http://www.ocac.gov.tw/" title="ocac" target="displaypage">&#20013;&#33775;&#27665;&#22283;&#20689;&#21209;&#22996;&#21729;&#26371;</a></li>
     <li><a href="http://www.boca.gov.tw/" title="ocac" target="displaypage">&#22806;&#20132;&#37096;&#38936;&#20107;&#20107;&#21209;&#23616;</a></li>
     <li><a href="http://www.teco.org/" title="ocac" target="displaypage">&#39376;&#20126;&#29305;&#34349;&#22823;&#21488;&#21271;&#32147;&#28639;&#25991;&#21270;&#36774;&#20107;&#34389;</a></li>

     </ul>
    </li>

       
    </ul>
    </li>

   

</ul></div>

</body>

</html>

```Heres yours:
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
    <link rel="stylesheet" type="text/css" media="screen" href="http://www.bmoore.net/css/menuExpandable.css" />    
    <script type="text/javascript" src="http://www.bmoore.net/scripts/menuExpandable.js"></script>
    <base target="_self">
</head>
<body>
<div id="menuDiv">
    <ul id="menuList">
    <li class="menubar"><a href="" id="FileActuator1" class="actuator">Advanced Placement Courses:</a>
        <ul id="FileMenu1" class="menu">
        <li><a href="" target="displaypage" onclick="greet()">American History</a></li>
        <li><a href="" target="displaypage" onclick="greet()">Economics</a></li>
        <li><a href="" target="displaypage" onclick="greet()">European History</a></li>
        <li><a href="" target="displaypage" onclick="greet()">Psychology</a></li>
        <li><a href="" target="displaypage" onclick="greet()">United States Government and Politics</a></li>
        </ul>
    </li>
    <li class="menubar"><a href="" id="FileActuator2" class="actuator">American Experience</a></li>
    <li class="menubar"><a href="" id="FileActuator3" class="actuator">American Politics</a></li>
    <li class="menubar"><a href="" id="FileActuator4" class="actuator">Criminology</a></li>
    <li class="menubar"><a href="" id="FileActuator5" class="actuator">Current World Issues</a></li>
    <li class="menubar"><a href="" id="FileActuator6" class="actuator">Economics</a></li>
    <li class="menubar"><a href="" id="FileActuator7" class="actuator">Geopolitical Studies</a></li>
    <li class="menubar"><a href="" id="FileActuator8" class="actuator">Global Studies</a></li>
    <li class="menubar"><a href="" id="FileActuator9" class="actuator">Psychology</a></li>
    <li class="menubar"><a href="" id="FileActuator10" class="actuator">Senior Social Studies</a></li>
    <li class="menubar"><a href="" id="FileActuator11" class="actuator">Sociology</a></li>
    <li class="menubar"><a href="" id="FileActuator12" class="actuator">The Science of Human Behavior</a></li>
    <li class="menubar"><a href="" id="FileActuator13" class="actuator">United States History</a></li>
    <li class="menubar"><a href="" id="FileActuator14" class="actuator">United States History from 1945</a></li>
    <li class="menubar"><a href="" id="FileActuator15" class="actuator">Western Civilizations</a>
        <ul id="FileMenu15" class="menu">
        <li><a href="" target="displaypage" onclick="greet()">Antiquity to Charlemagne</a></li>
        <li><a href="" target="displaypage" onclick="greet()">Renaissance to the 1870's</a></li>
        </ul>
    </li>
    <li class="menubar"><a href="" id="FileActuator16" class="actuator">World Regional Geography</a></li>
    </ul>
</div>
</body>
</html>
```

It doesn't look like you have added the "submenus"take a look ot the first "CODE", you should see it easily :)

---

### Post by moore.bryan on 2008-08-29
yeah... i checked that. turns-out it was something even more basic: an unclosed anchor. stupid, stupid, stupid...

---

### Post by gjoellee on 2008-08-29
Well...it is really easy to make mistakes when making/editing scripts:)

---

