# Clockwork
Clockwork Crossplatform Framework provides crossplatform scripting, networking, file I/O, and many other features for Unix, Windows, and Macintosh operating systems. Build once, run anywhere. This was built many years ago and even supports pre-OSX Macintosh operating systems. 

### C-Like Scripting Language...
Sample dartboard script. Can be changed and recompiled on the fly without having to restart the application.

```
INT throw, hit, score;
STRING grabch, grabro, throwch, throwro;

grabch = "You grab the three darts and step back to the line on the floor.";
grabro = "$n grabs three darts off $p and steps back to the line on the floor.";
act_to_char(grabch, ch, obj, NULL);
act_to_room(grabro, ch, obj, NULL);
wait(1);
throw = 1;
score = 0;
while(throw <= 3)
{
   if(throw == 1){
      act_to_char("You throw the first dart.", ch, obj, NULL);
      act_to_room("$n throws the first dart.", ch, obj, NULL);
   }else
   if(throw == 2){
      act_to_char("You throw the second dart.", ch, obj, NULL);
      act_to_room("$n throws the second dart.", ch, obj, NULL);
   }else
   if(throw == 3){
      if((random(1, 3)) == 1){
         act_to_char("You offer a prayer in hopes of a good throw.", ch, obj, NULL);
         act_to_room("$n mumbles a little prayer under $s breath.", ch, obj, NULL);
         wait(1);
      }
      act_to_char("You throw the last dart.", ch, obj, NULL);
      act_to_room("$n throws the last dart.", ch, obj, NULL);
   }

   hit = random(1, 4);
   if(hit == 1){
      send_room("It hits the bullseye!! 10 points!", room);
      score += 10;
   }else
   if(hit == 2){
      send_room("It hits the inner ring, 5 points", room);
      score += 5;
   }else
   if(hit == 3){
      send_room("It hits the middle ring, 3 points", room);
      score += 3;
   }else
   if(hit == 4){
      send_room("It hits the outer ring, 1 lousy point", room);
      score += 1;
   }
   if(throw != 3) wait(1);
   throw = throw + 1;
}
```
For further examples on how to use the scripting functionality see the implementation in the [OrangeMUD project](https://github.com/nolancs/OrangeMUD). 
