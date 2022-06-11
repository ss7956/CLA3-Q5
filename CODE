#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

unsigned int powmod(unsigned long long base, unsigned int exponent, unsigned int modulo)
{
  unsigned long long result = 1;
  while (exponent > 0)
  {
    if (exponent % 2 == 1)
    {
      result = (result * base) % modulo;
      exponent--;
    }
    else
    {
      base = (base * base) % modulo;
      exponent /= 2;
    }
  }
  return result;
}

unsigned int inverseModulo(unsigned int a, unsigned int modulo)
{
  return powmod(a, modulo - 2, modulo);
}

int main()
{
  unsigned int tests;
  scanf("%i", &tests);
  while (tests--)
  {
    unsigned long long n;
    scanf("%llu", &n);

    // sum along the diagonals, initially for width = 1
    unsigned long long sum = 1;
      
    unsigned long long x = n / 2;
    const unsigned int Modulo = 1000000007;

    x %= Modulo;

    // first part: 8 * x * (x + 1) * (2*x + 1) / 3
    //           = 4 *  sharedTerm * (2*x + 1) / 3
    unsigned long long sharedTerm = (2*x * (x + 1)) % Modulo;

    // the division by 3 becomes a multiplication by its modulo multiplicative inverse
    unsigned long long sum1 = ((4 * sharedTerm * (2*x + 1)) % Modulo) * inverseModulo(3, Modulo);

    // second part: 2 * x * (x + 1)      + 4 * x + 1
    //            =     secondTerm       + 4 * x + 1
    unsigned long long sum2 = sharedTerm + 4*x + 1;

    // sum = first part + second part
    sum = (sum1 % Modulo + sum2 % Modulo) % Modulo;

    printf("%d", sum);
    printf("\n");
  }
  return 0;
}
