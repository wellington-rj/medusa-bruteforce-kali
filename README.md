# Projeto: Ataques de Força Bruta com Medusa no Kali Linux

## Descrição Geral

Este projeto faz parte do bootcamp de cibersegurança da DIO, utilizando
**Kali Linux**, **Medusa**, **Metasploitable 2** e **DVWA** para simular
ataques controlados de força bruta.\
O objetivo é entender vulnerabilidades, explorar serviços comuns (FTP,
SMB, formulários web) e documentar boas práticas de mitigação.

------------------------------------------------------------------------

##  Ambiente Utilizado

-   **Kali Linux** (Máquina atacante)
-   **Metasploitable 2** (Máquina vítima)
-   **DVWA** - Damn Vulnerable Web Application (dentro do
    Metasploitable)
-   Rede: **Host-Only / Interna**\
-   Ferramentas:
    -   `nmap`
    -   `medusa`
    -   `enum4linux`
    -   `smbclient`
    -   Wordlists personalizadas

------------------------------------------------------------------------


## 🔍 1. Enumeração de Serviços com Nmap

O primeiro passo foi identificar portas abertas e serviços vulneráveis
na VM Metasploitable.

### Comando utilizado:

    nmap -sV -O <ip_da_máquina>

### Evidência:

![Enumeração](images/enumeração.png)

------------------------------------------------------------------------

## 🔐 2. Ataque de Força Bruta em FTP com Medusa

Após identificar a porta **21 (FTP)** aberta, realizamos um ataque de
força bruta usando o Medusa.

### Comando utilizado:

    medusa -h <ip> -u admin -P wordlists.txt -M ftp

### Evidência:

![FTP](images/82deaad9-terminal.png)

------------------------------------------------------------------------

## 🌐 3. Automação de Força Bruta em Formulário Web (DVWA)

Foi utilizado o DVWA em nível "LOW", permitindo ataques básicos a
formulários vulneráveis.

### Acesso ao DVWA:

    http://<ip>/dvwa

### Evidência:

![Form Web](images/formweb.png)

------------------------------------------------------------------------

## 📂 4. Password Spraying + Enumeração SMB

Enumeramos usuários do ambiente e realizamos tentativas via SMB usando:

### Comando para enumeração:

    enum4linux -a <ip>

### Acesso SMB:

    smbclient //<ip>/tmp -U guest

### Evidências:

![Enum SMB](images/enumeração.png)\
![SMBClient](images/smbclient.png)

------------------------------------------------------------------------

## 📝 Wordlist utilizada

Criamos uma wordlist simples como parte do aprendizado:

    admin
    password
    123456
    toor
    kali

------------------------------------------------------------------------

## 🛡️ Medidas de Mitigação

-   Desabilitar serviços desnecessários\
-   Configurar bloqueio de tentativas (fail2ban, IPTables)\
-   Implementar autenticação multifator (MFA)\
-   Utilizar senhas fortes e políticas de expiração\
-   Restringir acesso por firewall\
-   Monitorar logs de autenticação

------------------------------------------------------------------------

## 📬 Conclusão

Este projeto reforça o aprendizado prático sobre:

-   Ataques de força bruta em serviços reais\
-   Vulnerabilidades comuns em ambientes Linux\
-   Utilização do Medusa para auditoria\
-   Importância de boas práticas de segurança

A experiência prática em laboratório seguro é essencial para compreender
ataques e aprender a se defender deles.

------------------------------------------------------------------------

## 🔗 Autor

Projeto criado para fins educacionais no bootcamp da DIO.
