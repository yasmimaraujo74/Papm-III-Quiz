 // Lista de questões
const questions = [
  {question: "1. Antes de iniciar o exame físico respiratório, a primeira conduta correta é:", options: ["A) Solicitar que o paciente deite imediatamente","B) Cumprimentar, se identificar e pedir permissão para examinar","C) Iniciar ausculta sem explicações","D) Pedir para tossir antes do exame"], answer: "B"},
  {question: "2. Para realizar a inspeção do tórax, o ideal é que o paciente esteja:", options: ["A) Sentado, se possível","B) Em pé obrigatoriamente","C) Deitado em decúbito lateral","D) Curvado para frente"], answer: "A"},
  {question: "3. Na ectoscopia geral respiratória, deve-se avaliar:", options: ["A) Edema de membros inferiores apenas","B) Pupilas e reflexos","C) Anemia, cianose e baqueteamento digital","D) Glicemia capilar"], answer: "C"},
  {question: "4. Qual dos seguintes é um tipo de tórax descrito no roteiro?", options: ["A) Escavado renal","B) Tórax em tonel","C) Tórax abdominal","D) Tórax hiperdenso"], answer: "B"},
  {question: "5. Na inspeção estática, deve-se observar:", options: ["A) Simetria do tórax","B) Reflexo patelar","C) Marcha","D) Pressão arterial"], answer: "A"},
  {question: "6. Na inspeção dinâmica, avalia-se:", options: ["A) Ritmo ventilatório","B) Pulsos periféricos","C) Estado mental","D) Diurese"], answer: "A"},
  {question: "7. O tipo respiratório normal descrito no roteiro é:", options: ["A) Costal puro","B) Toracoabdominal","C) Paradoxal","D) Apneico"], answer: "B"},
  {question: "8. Frequência respiratória normal pode ser descrita como paciente:", options: ["A) Bradicárdico","B) Taquicárdico","C) Eupneico","D) Hipotenso"], answer: "C"},
  {question: "9. Antes da palpação do tórax, deve-se perguntar:", options: ["A) Se já operou o abdome","B) Se sente dor em alguma área","C) Se está em jejum","D) Se usa óculos"], answer: "B"},
  {question: "10. Durante a palpação, procura-se:", options: ["A) Sopros cardíacos","B) Áreas dolorosas e nódulos","C) Glicose baixa","D) Rigidez nucal"], answer: "B"},
  {question: "11. Se houver área dolorosa relatada, ela deve ser palpada:", options: ["A) Primeiro e com força","B) Por último e com cuidado","C) Apenas no dia seguinte","D) Nunca deve ser palpada"], answer: "B"},
  {question: "12. A elasticidade torácica anteroposterior é avaliada com:", options: ["A) Percussão digital","B) Pressão simétrica com as mãos","C) Ausculta lateral","D) Inspeção visual apenas"], answer: "B"},
  {question: "13. O resultado normal da palpação torácica é:", options: ["A) Tórax doloroso e rígido","B) Tórax indolor e elasticidade preservada","C) Tórax instável","D) Tórax hipertimpânico"], answer: "B"},
  {question: "14. Na expansibilidade dos lobos superiores anteriores, os polegares ficam:", options: ["A) Separados no ombro","B) Unidos na linha média","C) Sobre as costelas inferiores","D) Na região lombar"], answer: "B"},
  {question: "15. Durante a manobra de expansibilidade, o paciente deve:", options: ["A) Prender a respiração","B) Respirar superficialmente","C) Inspirar e expirar amplamente com boca aberta","D) Tossir repetidamente"], answer: "C"},
  {question: "16. A expansibilidade normal dos lobos superiores é predominantemente:", options: ["A) Lateral","B) Craniocaudal","C) Abdominal","D) Unilateral"], answer: "B"},
  {question: "17. Na região anterior inferior, avalia-se principalmente:", options: ["A) Traqueia","B) Lobo médio e língula","C) Pleura apical","D) Clavícula"], answer: "B"},
  {question: "18. Na região posterior inferior, avaliam-se:", options: ["A) Bases pulmonares","B) Cordas vocais","C) Escápulas","D) Seios da face"], answer: "A"},
  {question: "19. A expansibilidade normal da região inferior é:", options: ["A) Restrita e dolorosa","B) Predominantemente lateral e ampla","C) Ausente","D) Apenas unilateral"], answer: "B"},
  {question: "20. Para avaliar o frêmito tóraco-vocal utiliza-se:", options: ["A) Face palmar dos dedos","B) Dorso da mão","C) Martelo neurológico","D) Estetoscópio"], answer: "A"},
  {question: "21. O FTV deve ser examinado no sentido:", options: ["A) Horizontal puro","B) Craniocaudal","C) Circular","D) Aleatório"], answer: "B"},
  {question: "22. A palavra repetida pelo paciente no FTV é:", options: ["A) Vinte e dois","B) Quarenta e quatro","C) Trinta e três","D) Cinquenta e cinco"], answer: "C"},
  {question: "23. O achado normal do FTV é:", options: ["A) Ausente bilateralmente","B) Presente e simétrico","C) Apenas à direita","D) Apenas posterior"], answer: "B"},
  {question: "24. Na percussão torácica, o dedo apoiado no espaço intercostal é o:", options: ["A) 1º dedo","B) 2º dedo","C) 3º dedo","D) 5º dedo"], answer: "C"},
  {question: "25. O som normal à percussão pulmonar é:", options: ["A) Maciço","B) Timpânico","C) Claro e atimpânico","D) Metálico"], answer: "C"},
  {question: "26. Regiões escapulares costumam ser evitadas na percussão porque:", options: ["A) São dolorosas sempre","B) Alteram o som pela musculatura e osso","C) Não possuem pulmão","D) São infectadas"], answer: "B"},
  {question: "27. Na ausculta pulmonar utiliza-se:", options: ["A) Campânula obrigatoriamente","B) Diafragma do estetoscópio","C) Martelo reflexo","D) Oxímetro"], answer: "B"},
  {question: "28. O paciente deve respirar na ausculta de forma:", options: ["A) Boca fechada e rápida","B) Superficial e nasal","C) Profunda, boca aberta","D) Em apneia"], answer: "C"}


 }
];

// Renderiza as questões
const quizContainer = document.getElementById("quiz-container");

questions.forEach((q, index) => {
  const div = document.createElement("div");
  div.classList.add("question");

  div.innerHTML = `
    <p>${q.question}</p>
    ${q.options.map(opt => `
      <label>
        <input type="radio" name="q${index}" value="${opt.charAt(0)}"> ${opt}
      </label><br>
    `).join("")}
  `;

  quizContainer.appendChild(div);
});

// Verifica respostas
function checkAnswers() {
  let score = 0;

  questions.forEach((q, index) => {
    const selected = document.querySelector(`input[name="q${index}"]:checked`);
    if (selected && selected.value === q.answer) {
      score++;
    }
  });

  document.getElementById("result").textContent =
    `Você acertou ${score} de ${questions.length} questões.`;
}
