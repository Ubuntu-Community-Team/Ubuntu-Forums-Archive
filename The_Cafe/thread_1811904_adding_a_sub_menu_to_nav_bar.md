---
title: "adding a sub menu to nav bar"
date: 2011-07-25
forum: The Cafe
---

### Post by rmcellig on 2011-07-25
How can I add submenus under the Radio Shows item?
 This is the code I am using:


<code>

<script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.4.3/jquery.min.js"></script>

 <script>
 $(document).ready(function(){

   // hide #back-top first
    $("#back-top").hide();
   $("#top-divider").hide();

   // fade in #back-top
    $(function () {
     $(window).scroll(function () {
       if ($(this).scrollTop() > 100) {
         $('#back-top').show();
         $('#top-divider').show();
       } else {
         $('#back-top').hide();
         $('#top-divider').hide();
     }
 });

     // scroll body to 0px on click
     $('#back-top').click(function () {
       $('body,html').animate({
         scrollTop: 0
       }, 800);
       return false;
     });
   });

 });
 </script>

 <div id="topbar">

   <span style="float:left;padding-left:7px;">

     <span style="width:30px;"><a href="#" id="back-top" onclick="return false;">BACK TO TOP</a></span>

     <span id="letters" style="display:none;"><span  id="top-divider">&nbsp;|&nbsp;</span><a  href="#a">A</a>&nbsp;&nbsp;<a  href="#b">B</a>&nbsp;&nbsp;<a  href="#c">C</a>&nbsp;&nbsp;<a  href="#d">D</a>&nbsp;&nbsp;<a  href="#e">E</a>&nbsp;&nbsp;<a  href="#f">F</a>&nbsp;&nbsp;<a  href="#g">G</a>&nbsp;&nbsp;<a  href="#h">H</a>&nbsp;&nbsp;<a  href="#i">I</a>&nbsp;&nbsp;<a  href="#j">J</a>&nbsp;&nbsp;<a  href="#k">K</a>&nbsp;&nbsp;<a  href="#l">L</a>&nbsp;&nbsp;<a  href="#m">M</a>&nbsp;&nbsp;<a  href="#n">N</a>&nbsp;&nbsp;<a  href="#o">O</a>&nbsp;&nbsp;<a  href="#p">P</a>&nbsp;&nbsp;<a  href="#q">Q</a>&nbsp;&nbsp;<a  href="#r">R</a>&nbsp;&nbsp;<a  href="#s">S</a>&nbsp;&nbsp;<a  href="#t">T</a>&nbsp;&nbsp;<a  href="#u">U</a>&nbsp;&nbsp;<a  href="#v">V</a>&nbsp;&nbsp;<a  href="#w">W</a>&nbsp;&nbsp;<a  href="#x">X</a>&nbsp;&nbsp;<a  href="#y">Y</a>&nbsp;&nbsp;<a  href="#z">Z</a>&nbsp;</span>

   </span>

   <span style="float:right;padding-right:7px;">

 <a href="http://www.mcran.com" target="_self"><b>HOME</b></a>&nbsp;|&nbsp;

 <a href="http://www.mcran.com/bio-test-page.php" target="_self"><b>BIO</b></a>&nbsp;|&nbsp;
 
  <a href="http://www.mcran.com/contact.php" target="_self"><b>CONTACT</b></a>&nbsp;|&nbsp;

 <a href="http://www.mcran.com/interviews.php" target="_self"><b>INTERVIEWS</b></a>&nbsp;|&nbsp;

 <a href="http://www.mcran.com/playlistsshowtable.php"  target="_self"><b>PLAYLISTS</b></a>&nbsp;|&nbsp;

 <a href="http://www.mcran.com/2010-2006showstable.php"  target="_self"><b>RADIO  SHOWS</b></a>&nbsp;|&nbsp;

 <a href="http://www.mcran.com/favorite-sites.php"  target="_self"><b>RESOURCES</b></a>&nbsp;|&nbsp;

 
   </span>
  </div>

</code>

---

