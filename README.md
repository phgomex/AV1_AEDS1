#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
    srand(time(NULL));

    int portaPremiada, portaVazia, portaEscolhida;
    char opcao;

    printf("Bem-vindo ao jogo Monty Hall!\n");
    printf("Escolha uma porta (1, 2 ou 3): ");
    scanf("%d", &portaEscolhida);

    portaPremiada = rand() % 3 + 1;

    do {
        portaVazia = rand() % 3 + 1;
    } while (portaVazia == portaEscolhida || portaVazia == portaPremiada);

    printf("O apresentador abriu a porta %d que está vazia.\n", portaVazia);
    printf("Você deseja trocar para a outra porta? (s/n): ");
    scanf(" %c", &opcao);

    if (opcao == 's') {
        do {
            portaEscolhida = rand() % 3 + 1;
        } while (portaEscolhida == portaVazia || portaEscolhida == portaEscolhida);
    }

    if (portaEscolhida == portaPremiada) {
        printf("Você ganhou! Parabéns!\n");
    } else {
        printf("Você perdeu. A porta premiada era a %d.\n", portaPremiada);
    }

    return 0;
}
