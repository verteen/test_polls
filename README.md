# Open Source


##Подход с разными репозиториями для origin и для upstream:
1. fork a repo (на сайте github): https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY
2. скопировать ссылку из своего репозитория (не из исходного): https://github.com/YOUR_USERNAME/YOUR_FORK.git 
3. git clone https://github.com/YOUR_USERNAME/YOUR_FORK.git 
4. git remote -v 
	- должно показать 2 ветки origin:
	> origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)

	> origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
	
5. git remote add upstream https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git
6. git remote -v
	- должно показать 4 ветки: 2 origin и 2 upstream:
	> upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (fetch)

	> upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (push)
	
7. Что с этим всем делать? В такой модели для того, чтобы синхронизировать свой форк с исходной репой - надо перед изменениями делать последовательность команд:
	- git fetch upstream # вытянули изменения
	- git checkout master # переключились на master своего форка 
	- git merge upstream/master # слили изменения со своим форком

##Подход с одним репозиторием, но разными источниками для fetch и push:
1. fork a repo (на сайте github): https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY
2. скопировать ссылку из своего репозитория (не из исходного): https://github.com/YOUR_USERNAME/YOUR_FORK.git 
3. git clone https://github.com/YOUR_USERNAME/YOUR_FORK.git 
4. git remote -v 
	- должно показать 2 ветки origin:
	> origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)

	> origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
	
5. git remote set-url --push https://github.com/YOUR_USERNAME/YOUR_FORK.git
6. git remote -v 
	- должно показать 2 ветки origin: 
	- 
	> upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (fetch)

	> upstream  https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
	
7. Здесь для синхронизации ничего не надо делать - по умолчанию git fetch будет вытягивать последнюю версию из оригинальной репы, а git push - будет класть изменения к себе в форк

8. Минус такого подхода - в том, что более сложное разрешение конфликтов. При локальном разрешении конфликтов github не даст сделать git push, так как в удаленном репозитории не будет тех коммитов, что вы сделали локально.
В этом случае надо только создавать на сайте pull request и мейнтейнер должен его принять.




Доступные опросы:  
- [Сколько тебе лет?](polls/age/question.md)
- [Какой язык программирования для тебя основной?](polls/language/question.md)  
