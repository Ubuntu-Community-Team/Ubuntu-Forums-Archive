---
title: "serving HTML5 with apache2?"
date: 2010-12-28
forum: Server Platforms
---

### Post by Crazedpsyc on 2010-12-28
I just started playing with HTML5, and found a complete example. I downloaded it and double-clicked the index.html file. It opened up in firefox (4b9pre) just as it was supposed to, and it looked great! Then I copied it directly to a subdirectory of my apache server (/var/www/examples/html5/).
When I went to it in a browser ([http://localhost/examples/html5/index.html](http://localhost/examples/html5/index.html)) it was completely messed up (there were no organizational attributes anymore, everything was lined up on the left side in a few jumbled columns)

Any AddHandler I need to add or anything to get it to work?

Here is the html5 source:
```
<!DOCTYPE html> <html lang="en"> <head> <meta charset="utf-8"> <title>Page Title</title>  <!-- meta tags --> <meta name="keywords" content=""> <meta name="description" content="">  <!-- stylesheets --> <link rel="stylesheet" href="[css/reset.css]("http://ubuntuforums.org/view-source:http://bz/css/reset.css")" type="text/css"> <link rel="stylesheet" href="[css/common.css]("http://ubuntuforums.org/view-source:http://bz/css/common.css")" type="text/css"> <link rel="stylesheet" href="[css/layout.css]("http://ubuntuforums.org/view-source:http://bz/css/layout.css")" type="text/css">  <!-- javascript --> <script src="[js/jquery-1.3.2.min.js]("http://ubuntuforums.org/view-source:http://bz/js/jquery-1.3.2.min.js")"></script>  <!--conditional comments --> <!--[if IE]>   	<script src="js/html5.js"></script> <![endif]-->   </head> <body class="home"> <div id="container"> 	<header id="page-header">     	<div id="logo"><a href="[/]("http://ubuntuforums.org/view-source:http://bz/")"><img src="[images/graphic-logo.gif]("http://ubuntuforums.org/view-source:http://bz/images/graphic-logo.gif")" alt="Company Name"></a></div>         <nav id="main-navigation">         	<ul>             	<li class="current"><a href="[#]("http://ubuntuforums.org/view-source:http://bz/html5.html#")">Home</a></li>                 <li style="color: red;"><a href="[#]("http://ubuntuforums.org/view-source:http://bz/html5.html#")">About</a></li>                 <li><a href="[#]("http://ubuntuforums.org/view-source:http://bz/html5.html#")">Services</a></li>                 <li><a href="[#]("http://ubuntuforums.org/view-source:http://bz/html5.html#")">Portfolio</a></li>                 <li><a href="[#]("http://ubuntuforums.org/view-source:http://bz/html5.html#")">Contact</a></li>             </ul>         </nav>     </header>     <article id="page-content">         <section>             <hgroup>                 <h1>Demonstration of Using HTML5</h1>                 <h2>An HTML5 Template</h2>             </hgroup>             <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus ac iaculis erat. Maecenas id fermentum odio. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Fusce sagittis porta mauris, iaculis egestas metus posuere sit amet. Sed ullamcorper orci eu dolor egestas sodales. Donec tempor aliquet pulvinar. Sed sed turpis sapien, ac dictum sem. Phasellus metus leo, gravida in imperdiet sit amet, bibendum id magna. Vivamus ac nunc tortor. Lorem ipsum dolor sit amet, consectetur adipiscing elit. In quis justo ligula. Suspendisse sodales ultricies consequat. Aenean condimentum eros mi. Duis consectetur placerat vehicula. Fusce vel massa erat.</p>             <h2>A demonstration of list items</h2>             <ul>                 <li>Lorem ipsum dolor sit amet</li>                 <li>Lorem ipsum dolor sit amet</li>                 <li>Lorem ipsum dolor sit amet</li>                 <li>Lorem ipsum dolor sit amet</li>                 <li>Lorem ipsum dolor sit amet</li>             </ul>             <ol>                 <li>Lorem ipsum dolor sit amet</li>                 <li>Lorem ipsum dolor sit amet</li>                 <li>Lorem ipsum dolor sit amet</li>                 <li>Lorem ipsum dolor sit amet</li>                 <li>Lorem ipsum dolor sit amet</li>             </ol>          </section>         <aside>	             <h2>Related Content</h2>             <p>Aliquam id lorem ac tellus fringilla bibendum et at turpis. In ut auctor justo. Integer ac quam sed est semper hendrerit. Aenean vulputate interdum augue, sed dapibus mi ultricies convallis. Curabitur a nunc nisi, ac ornare nisi. Ut semper placerat accumsan. Cras eu nibh lorem. Sed sit amet ligula vitae orci molestie sollicitudin sit amet at odio. Mauris non elit ac ipsum facilisis eleifend. Maecenas eu velit sit amet neque iaculis dapibus. Integer mollis est id erat dignissim blandit. Quisque malesuada mattis sollicitudin. Pellentesque volutpat pellentesque luctus. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed cursus augue ut sem convallis ullamcorper. Donec vitae magna nec lacus varius pellentesque vel nec diam. Morbi sagittis, magna sit amet sollicitudin ultricies, neque orci fermentum ipsum, non cursus lectus velit at ante. Donec nec neque in sem suscipit faucibus. Aliquam nisi turpis, volutpat quis suscipit in, varius vitae nunc.</p>         </aside>     </article>           </div> <footer> 	&copy; Copyright Dave Woods 2009	 </footer> </body> </html> 
```

---

### Post by windependence on 2010-12-28
You didn't put the style sheet in the directory, it's NOT an Apache issue. You need to put all .css files in the directory with the html. Apache will serve anything you want it to, it doesn't care about the code.
 
 
-Tim

---

### Post by Crazedpsyc on 2010-12-28
Oh, it wasn't that I didn't copy it, I just copied it as root with "sudo cp -r css /var/www/examples/html5" so all I had to do was "sudo chmod a+r /var/www/examples/html5/css"!
Thanks!

---

