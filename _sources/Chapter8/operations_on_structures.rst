Operations on structures
------------------------

Most of the operators we have been using on other types, like
mathematical operators ( ``+``, ``%``, etc.) and comparison operators
(``==``, ``>``, etc.), do not work on structures. Actually, it is
possible to define the meaning of these operators for the new type, but
we won’t do that in this book.

On the other hand, the assignment operator *does* work for structures.
It can be used in two ways: to initialize the instance variables of a
structure or to copy the instance variables from one structure to
another. An initialization looks like this:

::

     Point blank = { 3.0, 4.0 };

The values in squiggly braces get assigned to the instance variables of
the structure one by one, in order. So in this case, ``x`` gets the
first value and ``y`` gets the second.

Unfortunately, this syntax can be used only in an initialization, not in
an assignment statement. So the following is illegal.

::

     Point blank;
     blank = { 3.0, 4.0 };       // WRONG !!

You might wonder why this perfectly reasonable statement should be
illegal; I’m not sure, but I think the problem is that the compiler
doesn’t know what type the right hand side should be. If you add a
typecast:

::

     Point blank;
     blank = (Point){ 3.0, 4.0 };

That works.

It is legal to assign one structure to another. For example:

::

     Point p1 = { 3.0, 4.0 };
     Point p2 = p1;
     cout << p2.x << ", " <<  p2.y << endl;

The output of this program is ``3, 4``.

.. clickablearea:: operations_structures_1
    :question: Click on all incorrect statements.
    :iscode:
    :feedback: Remember, this syntax can be used only in an initialization, not in an assignment statement.

    :click-incorrect:int main() {:endclick:
        :click-incorrect:Point blank = { 3.0, 4.0 };:endclick:
        :click-incorrect:Point hello;:endclick:
        :click-correct:hello = { 3.0, 4.0 };:endclick:
        :click-incorrect:Point new;:endclick:
        :click-incorrect:Point p = hello;:endclick:
        :click-incorrect:new = (Point){3.0, 4.0};:endclick:
        :click-correct:bool check = blank == new;:endclick:
        :click-correct:new = {3.0, 4.0};:endclick:
    }

.. parsonsprob:: operations_structures_2
   :numbered: left
   :adaptive:

   Construct a block of code that correctly initializes the instance variables of a structure.
   -----
   struct Point {
   =====
       double x, y;
   =====
   };
   =====
   int main() {
   =====
       Point blank;
   =====
       int blank; #distractor
   =====
       blank = (Point){ 12.0, 3.2 };
   =====
       blank = (Point){ 12.0, 3.2 } #distractor
   =====
       blank = { 12.0, 3.2 }; #distractor
   =====
   }

.. mchoice:: operations_structures_3
   :multiple_answers:
   :answer_a: %
   :answer_b: =
   :answer_c: >
   :answer_d: ==
   :answer_e: +
   :correct: a, c, d, e
   :feedback_a: The modulo operator does not work on structures.
   :feedback_b: The assignment operator does work on structures.
   :feedback_c: The greater than operator does not work on structures.
   :feedback_d: The equality operator does not work on structures.
   :feedback_e: The addition operator does not work on structures.

   Which operators do NOT work on structures. Select all that apply.

