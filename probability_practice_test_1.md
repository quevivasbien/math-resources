### 1

Consider the names below

> ALEX MAGGIE MATTHEW AANISA

First, pick a name from this list (uniformly, i.e. each name is equally likely to be chosen) at random. Then pick a letter from the name (uniformly) at random. What is the probability that the character picked is an A?

### 2

a) Is it possible to have a random variable $X$ such that, for some $p \in [0,1]$ and for all $x \in \mathbb{N}$, $P(X=x) = p$? If so, give an example of such an $X$; if not, prove it.

b) Is it possible to have a random variable $X$ such that, for all $x \in \mathbb{N}$, $P(X=x) > 0$? If so, give an example; if not, prove it.

c) Would the random variables in parts (a) and (b) be considered discrete or continuous?

### 3

In the game of Yeetzah, players roll four fair twelve-sided dice.

(a) A "Yeetzah" occurs when all four dice show the same face. What is the probability of this happening in a given roll?

(b) A "straight" occurs when the numbers rolled are distinct and consecutive (e.g. 1, 2, 3, 4 or 5, 6, 7, 8). Note that the dice can be rearranged, so, for example, 4, 3, 1, 2 is also a straight. What is the probability that a given roll is a straight?

(c) What is the probability that all four dice in a given roll come out as different numbers?

(d) What is the probability of getting a three-of-a-kind (with the fourth roll distinct from the other three)?

### 4

Let $X$ be a continuous random variable with probability density function

$$f_X(x) = \left\{ \begin{array}{ll}
e^{cx}, & x \geq 0 \\
0, & x < 0
\end{array} \right.$$

What is the value of $c$?

### 5

Bobby the computer scientist is using an LSTM neural network to identify potential terrorists based on the status updates they post on Twitter. He is testing his latest neural network and found that 90% of Twitter users that are actually terrorists are predicted by his network to be terrorists, and that 2% of those who are not actually terrorists are predicted to be terrorists. He knows that approximately 0.005% of Twitter users are terrorists. Given that the neural network predicts that a randomly chosen Twitter user is a terrorist, what is the probability that this user is actually a terrorist?

## Solutions

Don't look at these unless you've already either solved the problems or are have absolutely no idea how to solve them (i.e. you've thought about them for a while, given them your best effort, slept on it, tried again, and still don't know what to do). Struggling with a problem is one of the best ways to learn and retain information.

### 1

One way to solve this is to recall the identity
$$P(A \cap B) = P(A | B) P(B)$$

The problem becomes

$$\begin{align}
P(A) =& \ P(\text{ALEX} \cap A) + P(\text{MAGGIE} \cap A)  \\
& + P(\text{MATTHEW} \cap A) + P(\text{AANISA} \cap A) \\
=& \ P(A | \text{ALEX}) P(\text{ALEX}) + P(A | \text{MAGGIE}) P(\text{MAGGIE})  \\
& +P(A | \text{MATTHEW}) P(\text{MATTHEW}) + P(A | \text{AANISA}) P(\text{AANISA}) \\
=& \ \left(\frac{1}{4}\right) \left(\frac{1}{4}\right) + \left(\frac{1}{6}\right) \left(\frac{1}{4}\right) + \left(\frac{1}{7}\right) \left(\frac{1}{4}\right) + \left(\frac{1}{2}\right) \left(\frac{1}{4}\right)\\
\end{align}$$

### 2

(a) No. Let $p \in [0, 1]$. If $p = 0$, then $\sum_{x \in \mathbb{N}} p = 0$. Otherwise $\sum_{x \in \mathbb{N}} p$ diverges to infinity. For $X$ to be a random variable, we need $\sum_{x \in \mathbb{N}} P(X=x) = 1$.

(b) Yes. For $x \in \mathbb{N}$, let $$P(X=x) = \frac{1}{2^x}.$$

(c) Discrete, not continuous.

### 3

(a) The total number of possible rolls is $12^4$. There are 12 different ways to get a "Yeetzah" (one for each number that could be rolled). So the probability of a "Yeetzah" is
$$\frac{12}{12^4}$$

(b) The first thing we need to figure out is how many sets of rolls there are that contain consecutive, distinct numbers. The possible sets are
$$\{1,2,3,4\}, \{2,3,4,5\}, \{3,4,5,6\}, \dots, \{9,10,11,12\}$$
There are 9 different sets that work. We need to remember that, since the order of the rolls doesn't matter as long as they all end up being distinct and consecutive, any ordering of the above sets is fine. The number of ways to order a set of 4 elements is
$$4! = 4 \cdot 3 \cdot 2 \cdot 1 = 24$$
So for each of the 9 allowable sets, there are 24 orderings that work. The total number of allowable options is therefore $9 \cdot 24$. Thus the probability of a straight is
$$\frac{9 \cdot 24}{12^4}$$

(c) One way to figure out the number of possible ways to get all four dice to be different is to think about assigning them numbers consecutively. There are 12 allowable options for the first die. For each of those 12 options, there are 11 remaining options for the second die. For each of those there are 10 for the third, and for each of those there are 9 for the fourth. The total number of allowable options is therefore $12 \cdot 11 \cdot 10 \cdot 9$. You can also think about this as a permutation problem: The number of possible orderings of $k$ items from $n$ total is $n!/(n-k)!$ In this case, we have $12!/8!$, which is equivalent to what we got before. At any rate, the probability is the number of allowable rolls divided by the number of total rolls, which is
$$\frac{12 \cdot 11 \cdot 10 \cdot 9}{12^4}$$

(d) There are 12 ways to chose the number that is repeated three times and for each of those ways, there are 11 ways to choose the other number. For each choice of numbers, there are 4 ways to arrange them (since the number rolled only once can go in one of four "spots"). So the number of ways to get three-of-a-kind is $12 \cdot 11 \cdot 4$, and the probability is
$$\frac{12 \cdot 11 \cdot 4}{12^4}$$

## 4

The PDF integrated over all real numbers must equal 1. Thus
$$1 = \int_{-\infty}^\infty f_X(x) dx = \int_0^\infty e^{cx} dx = \frac{1}{c} e^{cx} \Big|_0^\infty = -\frac{1}{c}$$

(Note that if $c$ is not negative, the integral diverges.) So $c = -1$.

## 5

Let's call $S$ the event that the neural network says that a Twitter user is a terrorist and $T$ the event that a Twitter user actually is a terrorist. We're given that $P(S|T) = 0.9$, $P(S|T^C) = 0.02$, and $P(T) = 0.00005.$ We want to find $P(T|S)$. We can use Bayes' theorem:
$$\begin{align}
P(T|S) &= \frac{P(S|T)P(T)}{P(S|T)P(T) + P(S|T^C)P(T^C)} \\
&= \frac{0.9 \cdot 0.00005}{0.9 \cdot 0.00005 + 0.02 \cdot 1.99995} \\
&\approx 0.002
\end{align}$$
