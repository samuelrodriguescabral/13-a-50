# 13-a-50

13
#include <stdio.h>

void exibirFibonacci(int n) {
    
    unsigned long long int a = 0, b = 1, c;
    
    
    if (n <= 0) {
        printf("O número de termos deve ser maior que 0.\n");
        return;
    }


    printf("Sequência de Fibonacci com %d termos:\n", n);
    
    for (int i = 1; i <= n; i++) {
        if (i == 1) {
            printf("%llu ", a);
        } else if (i == 2) {
            printf("%llu ", b);
        } else {
            c = a + b;  
            a = b;      
            b = c;
            printf("%llu ", c);
        }
    }
    printf("\n");
}

int main() {
    int termos;
    
    
    printf("Digite o número de termos da sequência de Fibonacci que deseja exibir: ");
    scanf("%d", &termos);
    
    
    exibirFibonacci(termos);
    
    return 0;
}

14

#include <stdio.h>

int inverterDigitos(int num) {
    int invertido = 0;

    while (num != 0) {
        int digito = num % 10;  
        invertido = invertido * 10 + digito; 
        num /= 10;  
    }

    return invertido;
}

int main() {
    int numero, numeroInvertido;

    
    printf("Digite um número inteiro: ");
    scanf("%d", &numero);

    
    numeroInvertido = inverterDigitos(numero);

    
    printf("Número invertido: %d\n", numeroInvertido);

    return 0;
}

15 

#include <stdio.h>


double calcularPotencia(double base, int expoente) {
    double resultado = 1.0;
    
    
    if (expoente < 0) {
        base = 1.0 / base;
        expoente = -expoente;
    }
    
    
    for (int i = 0; i < expoente; i++) {
        resultado *= base;
    }
    
    return resultado;
}

int main() {
    double base;
    int expoente;
    
    
    printf("Digite a base: ");
    scanf("%lf", &base);
    printf("Digite o expoente: ");
    scanf("%d", &expoente);
    
    
    double resultado = calcularPotencia(base, expoente);
    
    
    printf("%.2lf elevado a %d é igual a %.2lf\n", base, expoente, resultado);
    
    return 0;
}

16 

#include <stdio.h>
#include <string.h>
#include <ctype.h>


int verificarPalindromoPalavra(char str[]) {
    int inicio = 0;
    int fim = strlen(str) - 1;
    
    
    while (inicio < fim) {
        
        while (inicio < fim && !isalpha(str[inicio])) inicio++;
        while (inicio < fim && !isalpha(str[fim])) fim--;
        
        
        if (tolower(str[inicio]) != tolower(str[fim])) {
            return 0;  
        }
        
        inicio++;
        fim--;
    }
    
    return 1;  
}

int main() {
    char palavra[100];
    
    
    printf("Digite uma palavra ou frase: ");
    fgets(palavra, sizeof(palavra), stdin);
    
    
    palavra[strcspn(palavra, "\n")] = 0;
    
    
    if (verificarPalindromoPalavra(palavra)) {
        printf("\"%s\" é um palíndromo.\n", palavra);
    } else {
        printf("\"%s\" não é um palíndromo.\n", palavra);
    }
    
    return 0;
}

17

#include <stdio.h>


int calcularMDC(int a, int b) {
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

int main() {
    int a, b;
    printf("Digite dois números inteiros: ");
    scanf("%d %d", &a, &b);
    printf("O MDC de %d e %d é %d\n", a, b, calcularMDC(a, b));
    return 0;
}

18 

#include <stdio.h>


int calcularMDC(int a, int b) {
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}


int calcularMMC(int a, int b) {
    return (a * b) / calcularMDC(a, b);
}

int main() {
    int a, b;
    printf("Digite dois números inteiros: ");
    scanf("%d %d", &a, &b);
    printf("O MMC de %d e %d é %d\n", a, b, calcularMMC(a, b));
    return 0;
}

19

#include <stdio.h>


int verificarNumeroPerfeito(int num) {
    int soma = 0;
    for (int i = 1; i <= num / 2; i++) {
        if (num % i == 0) {
            soma += i;
        }
    }
    return soma == num;
}

int main() {
    int num;
    printf("Digite um número inteiro: ");
    scanf("%d", &num);
    if (verificarNumeroPerfeito(num)) {
        printf("%d é um número perfeito.\n", num);
    } else {
        printf("%d não é um número perfeito.\n", num);
    }
    return 0;
}
20
#include <stdio.h>


void ordenarVetor(int vetor[], int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (vetor[j] > vetor[j + 1]) {
                int temp = vetor[j];
                vetor[j] = vetor[j + 1];
                vetor[j + 1] = temp;
            }
        }
    }
}

int main() {
    int n;
    printf("Digite o número de elementos do vetor: ");
    scanf("%d", &n);
    
    int vetor[n];
    printf("Digite os elementos do vetor:\n");
    for (int i = 0; i < n; i++) {
        scanf("%d", &vetor[i]);
    }
    
    ordenarVetor(vetor, n);
    
    printf("Vetor ordenado:\n");
    for (int i = 0; i < n; i++) {
        printf("%d ", vetor[i]);
    }
    printf("\n");
    
    return 0;
}
21

#include <stdio.h>


int buscarLinear(int vetor[], int n, int chave) {
    for (int i = 0; i < n; i++) {
        if (vetor[i] == chave) {
            return i; 
        }
    }
    return -1; 
}

int main() {
    int n, chave;
    printf("Digite o número de elementos do vetor: ");
    scanf("%d", &n);
    
    int vetor[n];
    printf("Digite os elementos do vetor:\n");
    for (int i = 0; i < n; i++) {
        scanf("%d", &vetor[i]);
    }
    
    printf("Digite o valor a ser buscado: ");
    scanf("%d", &chave);
    
    int resultado = buscarLinear(vetor, n, chave);
    
    if (resultado != -1) {
        printf("O valor %d foi encontrado no índice %d.\n", chave, resultado);
    } else {
        printf("O valor %d não foi encontrado no vetor.\n", chave);
    }
    
    return 0;
}
22 
#include <stdio.h>


int buscarBinaria(int vetor[], int n, int chave) {
    int esquerda = 0;
    int direita = n - 1;
    
    while (esquerda <= direita) {
        int meio = esquerda + (direita - esquerda) / 2;
        
        if (vetor[meio] == chave) {
            return meio; 
        }
        
        if (vetor[meio] < chave) {
            esquerda = meio + 1;
        } else {
            direita = meio - 1;
        }
    }
    return -1; 
}

int main() {
    int n, chave;
    printf("Digite o número de elementos do vetor: ");
    scanf("%d", &n);
    
    int vetor[n];
    printf("Digite os elementos do vetor (ordenados):\n");
    for (int i = 0; i < n; i++) {
        scanf("%d", &vetor[i]);
    }
    
    printf("Digite o valor a ser buscado: ");
    scanf("%d", &chave);
    
    int resultado = buscarBinaria(vetor, n, chave);
    
    if (resultado != -1) {
        printf("O valor %d foi encontrado no índice %d.\n", chave, resultado);
    } else {
        printf("O valor %d não foi encontrado no vetor.\n", chave);
    }
    
    return 0;
}

23 
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
    int numeroSecreto, palpite, tentativas = 0;
    
    srand(time(0));
    numeroSecreto = rand() % 100 + 1; 
    
    printf("Tente adivinhar o número entre 1 e 100:\n");
    
    do {
        printf("Digite seu palpite: ");
        scanf("%d", &palpite);
        tentativas++;
        
        if (palpite < numeroSecreto) {
            printf("Muito baixo! Tente novamente.\n");
        } else if (palpite > numeroSecreto) {
            printf("Muito alto! Tente novamente.\n");
        } else {
            printf("Parabéns! Você adivinhou o número em %d tentativas.\n", tentativas);
        }
    } while (palpite != numeroSecreto);
    
    return 0;
}
24
#include <stdio.h>
#include <math.h>


int binarioParaDecimal(long binario) {
    int decimal = 0;
    int base = 1; 

    while (binario > 0) {
        int ultimoDigito = binario % 10;
        decimal += ultimoDigito * base;
        base *= 2;
        binario /= 10;
    }
    return decimal;
}

int main() {
    long binario;
    printf("Digite um número binário: ");
    scanf("%ld", &binario);
    printf("O número binário %ld em decimal é %d\n", binario, binarioParaDecimal(binario));
    return 0;
}
25
#include <stdio.h>


void decimalParaBinario(int num) {
    
    int binario[32];
    int i = 0;

    
    if (num == 0) {
        printf("0");
        return;
    }

    
    while (num > 0) {
        binario[i] = num % 2;
        num /= 2;
        i++;
    }

    
    printf("Representação binária: ");
    for (int j = i - 1; j >= 0; j--) {
        printf("%d", binario[j]);
    }
    printf("\n");
}

int main() {
    int numero;

    
    printf("Digite um número decimal: ");
    scanf("%d", &numero);

    
    if (numero < 0) {
        printf("Número negativo não é suportado.\n");
    } else {
        
        decimalParaBinario(numero);
    }

    return 0;
}
26

#include <stdio.h>

#define MAX 10  

void somaMatrizes(int matriz1[MAX][MAX], int matriz2[MAX][MAX], int resultado[MAX][MAX], int linhas, int colunas) {
    for (int i = 0; i < linhas; i++) {
        for (int j = 0; j < colunas; j++) {
            resultado[i][j] = matriz1[i][j] + matriz2[i][j];
        }
    }
}

int main() {
    int matriz1[MAX][MAX], matriz2[MAX][MAX], resultado[MAX][MAX];
    int linhas, colunas;

    printf("Digite o número de linhas e colunas: ");
    scanf("%d %d", &linhas, &colunas);

    printf("Digite os elementos da primeira matriz:\n");
    for (int i = 0; i < linhas; i++)
        for (int j = 0; j < colunas; j++)
            scanf("%d", &matriz1[i][j]);

    printf("Digite os elementos da segunda matriz:\n");
    for (int i = 0; i < linhas; i++)
        for (int j = 0; j < colunas; j++)
            scanf("%d", &matriz2[i][j]);

    somaMatrizes(matriz1, matriz2, resultado, linhas, colunas);

    printf("Resultado da soma das matrizes:\n");
    for (int i = 0; i < linhas; i++) {
        for (int j = 0; j < colunas; j++)
            printf("%d ", resultado[i][j]);
        printf("\n");
    }

    return 0;
}

27

#include <stdio.h>

#define MAX 10  

void multiplicacaoMatrizes(int matriz1[MAX][MAX], int matriz2[MAX][MAX], int resultado[MAX][MAX], int linhas1, int colunas1, int colunas2) {
    for (int i = 0; i < linhas1; i++) {
        for (int j = 0; j < colunas2; j++) {
            resultado[i][j] = 0;
            for (int k = 0; k < colunas1; k++) {
                resultado[i][j] += matriz1[i][k] * matriz2[k][j];
            }
        }
    }
}

int main() {
    int matriz1[MAX][MAX], matriz2[MAX][MAX], resultado[MAX][MAX];
    int linhas1, colunas1, linhas2, colunas2;

    printf("Digite o número de linhas e colunas da primeira matriz: ");
    scanf("%d %d", &linhas1, &colunas1);

    printf("Digite o número de linhas e colunas da segunda matriz: ");
    scanf("%d %d", &linhas2, &colunas2);

    if (colunas1 != linhas2) {
        printf("Não é possível multiplicar as matrizes. O número de colunas da primeira deve ser igual ao número de linhas da segunda.\n");
        return 1;
    }

    printf("Digite os elementos da primeira matriz:\n");
    for (int i = 0; i < linhas1; i++)
        for (int j = 0; j < colunas1; j++)
            scanf("%d", &matriz1[i][j]);

    printf("Digite os elementos da segunda matriz:\n");
    for (int i = 0; i < linhas2; i++)
        for (int j = 0; j < colunas2; j++)
            scanf("%d", &matriz2[i][j]);

    multiplicacaoMatrizes(matriz1, matriz2, resultado, linhas1, colunas1, colunas2);

    printf("Resultado da multiplicação das matrizes:\n");
    for (int i = 0; i < linhas1; i++) {
        for (int j = 0; j < colunas2; j++)
            printf("%d ", resultado[i][j]);
        printf("\n");
    }

    return 0;
}

28

#include <stdio.h>

int determinante2x2(int matriz[2][2]) {
    return matriz[0][0] * matriz[1][1] - matriz[0][1] * matriz[1][0];
}

int main() {
    int matriz[2][2];

    printf("Digite os elementos da matriz 2x2:\n");
    for (int i = 0; i < 2; i++)
        for (int j = 0; j < 2; j++)
            scanf("%d", &matriz[i][j]);

    printf("Determinante da matriz 2x2: %d\n", determinante2x2(matriz));

    return 0;
}

29

#include <stdio.h>
#include <ctype.h>

int contarVogais(const char* str) {
    int contagem = 0;
    while (*str) {
        char c = tolower(*str);
        if (c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u') {
            contagem++;
        }
        str++;
    }
    return contagem;
}

int main() {
    char str[100];

    printf("Digite uma string: ");
    fgets(str, sizeof(str), stdin); 

    printf("Número de vogais: %d\n", contarVogais(str));

    return 0;
}







