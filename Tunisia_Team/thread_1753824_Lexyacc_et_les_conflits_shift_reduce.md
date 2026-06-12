---
title: "Lex/yacc et les conflits shift reduce"
date: 2011-05-09
forum: Tunisia Team
---

### Post by Ibn_Al_Arabi on 2011-05-09
Assalamou alaykom ,

J'ai un problème avec Bison et les problèmes shift/reduce. Dans une  règle , quand j'ajoute un traitement après un terminal reconnu , j'ai  plus de conflits shift reduce.

```

signal_def :
        signal_name {
        std::string str ;
        std::string::iterator it;
        int i ;
        for (i=0;i<yylength-2 ;i++)
        str.insert(str.begin()+i,yytext[i+1]);
        temp_sig.SetName(str);
        if (Check_Signal_Exists(temp_sig))
        yyerror ("Signal already exists !");
        }
        direction {
        if (strcmp (yytext , "In" ))
            temp_sig.SetDir(In);
        else if (strcmp (yytext , "Out" ))
            temp_sig.SetDir(Out);
            else if (strcmp (yytext , "InOut" ))
            temp_sig.SetDir(InOut);
            else yyerror("Unknown Signal Direction");
        Store_Signal_Pin(temp_sig);
        }  ';'
        | signal_name direction
        '{'  signal_properties '}'
        ;

```
La j'ai 9 conflits shift/reduce alors que dans le cas suivant j'en ai 4 :
```

signal_def :
        signal_name direction {
        if (strcmp (yytext , "In" ))
            temp_sig.SetDir(In);
        else if (strcmp (yytext , "Out" ))
            temp_sig.SetDir(Out);
            else if (strcmp (yytext , "InOut" ))
            temp_sig.SetDir(InOut);
            else yyerror("Unknown Signal Direction");
        Store_Signal_Pin(temp_sig);
        }  ';'
        | signal_name direction
        '{'  signal_properties '}'
        ;

```

Quelqu'un a une idée ? ... Howa si ce n'était que de me dire qu'il ya plus de problèmes shift/reduce mouch mochkel mais le problème c'est que la première règle est ignorée !

Rabbi yberkelkom

---

