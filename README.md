# projeto gRPC

## gRPC

- **Framework**
- Facilita a comunicação entre sistemas
- Leve, independente e performático
- Criado pela Google, mantido pela CNCF

## Casos de Uso

- Ideal para microserviços
- Suporte em Mobile, Browsers (experimental) e Backend
- Geração automática de bibliotecas
- Streaming bidirecional usando HTTP/2

## Linguagens com Suporte Oficial

- GO
- Java
- C (e derivados)
  - C++
  - Python
  - Ruby
  - Objective C
  - PHP
  - C#
  - Node.js
  - Dart
- Kotlin

## RPC - Chamada Remota de Procedimento

- Cliente invoca um procedimento no servidor

## Protocol Buffers (Proto Buff)

- "XML muito menor, mais rápido e mais simples"
- Dados trafegam em binário
- Serialização e desserialização necessárias
- Menos uso de CPU no parsing
- Contrato definido por um arquivo proto

## Protocol Buffers vs JSON

- Arquivos binários < JSON (extremamente menor)
- Serialização mais leve que JSON
- Menos uso de recursos de rede
- Processo mais rápido devido ao protocolo mais recente

### Exemplo Proto Buff

```proto
syntax = "proto3";

message SearchRequest {
    string query = 1;
    int32 page_number = 2;
    int32 result_per_page = 3;
}

```

no caso ali string query = 1; representa: [tipo] [nome] = [ordem];

## HTTP/2:
	- Nome original criado pela Google era SPDY;
	- Lançado em 2015;
	- Dados trafegados são em binário e não texto como HTTP 1.1;
	- Utiliza a mesma conexão TCP para enviar e receber dados do cliente e do servidor (Multiplex);
	- Server Push (O servidor manda informações para todos que estão conectados nele);
	- Headers são comprimidos;
	- Gasta menos recursos de rede;
	- Processo é mais veloz;

## Formatos de comunicação 

- gRPC - API "unary" (implementado no projeto):
	- Cliente faz request e recebe response;
- gRPC - API "server streaming":
	-  Cliente faz request e pode receber uma ou várias response;
		- Para processos mais lentos e trabalhosos. Conforme o processo vai sendo resolvido ele dispara aos poucos os resultados;
- gRPC - API "client streaming" (implementado no projeto):
	- Client faz várias requests para o server e ele retorna uma response:
		- Para processos longos do lado do browser como processamento de grandes arquivos
- gRPC - API "bi directional streaming" (implementado no projeto):
	- Cliente manda várias requests para o servidor e o mesmo retorna várias responses;

## REST vs gRPC:
 - REST:
	- Texto/JSON;
 	- Unidirecional;
 	- Alta latência;
 	- Sem contrato (maior chance de erros)
 	- Sem suporte a streaming;
 	- Design pré-definido (tem os métodos definidos, padrão de url, no final do dia é um padrão de crud);
 	- Bibliotecas de terceiro para fazer conexões.
 - gRPC:
 	- Proto buffs;
 	- Bidirecional e assíncrono;
 	- Baixa latência;
 	- Contrato definido (.proto);
 	- Suporte a streaming;
 	- Design é livre;
 	- Geração de código (libs nativas == menos problemas).
