# userservice
Security Service Application Demo

Conceitos:
	Authentication: Verifies you are who you say you are
	Authorization: Decides if you have permissiion to access a resource

Passos:
	1. Montar o projeto com as seguintes dependencias:
		a. <artifactId>spring-boot-starter-data-jpa</artifactId>
		<artifactId>spring-boot-starter-security</artifactId>
		<artifactId>spring-boot-starter-web</artifactId>
		<artifactId>spring-boot-devtools</artifactId>
		<artifactId>postgresql</artifactId>
		<groupId>org.projectlombok</groupId>
		<artifactId>spring-boot-starter-test</artifactId>
		<artifactId>spring-security-test</artifactId>
		<dependency> (https://mvnrepository.com/artifact/com.auth0/java-jwt)
			<groupId>com.auth0</groupId>
			<artifactId>java-jwt</artifactId>
			<version>3.19.2</version>
		</dependency>
	2. Construir o Applicatoin
		a. Security
			i. Criar um Bean (@Bean) para BCcryptPassowordEncoder())
	3. Criar as Entidades (@Entity /@Data) de AppUser e Roles 
		a. Definição de campos
		b. Utilizar JPA com Postgress, atualizar o application.yml com conexões com DB
		c. Criar um database chamado userservices no pgAmin (http://localhost:5050/)
	4. Criar um Repositórios de Entidades (extends JpaRepository)
		a. Adicionar métodos findByName ou findByUsername;
	5. Criar um Serviço (@Service) para manipular as Entidades (CRUD)
		a. Implementar metodos do tipo saveUser, saveRole;
		b. Implementar uma interface e Implementação;
		c. Este Serviço deve utilizar os repositórios criados no passo anterior
		d. Segurança:
			i. Implementar a interface UserDetailsService
				1) Implementar o método loadUserByUsername
	6. Criar um Controller (@RestController) para expor APIs do tipo CRUD 
		a. Implementar os metodos saveUser, saveRoles, etc
		b. Este Controller deve utilizar o Serviço criado no passo anterior
	7. Criar uma comando de linha na Aplicação para inserir usuários e papeis no banco de dados;
		a. Utilizar o serviço criado nos passos anteriores;
	8. Criar uma classe d Configuração de segurança (@Configuration @EnableWebSecurity) and (extends WebSecurityConfgurerAdapter)
		a. Implementar configure(AtuhenticationManagerBuilder)
		b. Implementar configure (HttpSecurity)
	9. Criar os filtros para Autenticação (extends UsernamePasswordAuthenticationFilter)
		a. Implementar os metodos
			i. attemptAuthentication
			ii. successfulAuthentication
			iii. unsuccessfulAuthentication
	10. Criar Filtros para Autorização (extends OncePerRequestFilter)
		a. Estender os metodos
			i. doFilterInternal
	11. Configurar a classe SecurityConfig com as regras de segurança por enpoint do controller, 
		a. Adicioanar os Filtros de Authenticacao e Autorizacao
    b. A ordem importa.!
