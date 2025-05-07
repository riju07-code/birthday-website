const members = ['sandipan', 'abhi', 'mota', 'choyon', 'sayan'];
const days = ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday'];

function generateChoreRoutine() {
  let output = '🧼🍳🪣 Weekly Chore Routine (Room Cleaning, Cooking & Cooking Utensils)\n\n';

  let washIndex = 0;
  let cookIndex = 0;
  let pochaIndex = 0;

  days.forEach(day => {
    let roomCleaner, cook, cookingUtensils;

    // Assign Room Cleaning: Rotate among members
    roomCleaner = members[washIndex % members.length];
    washIndex++;

    // Exclude roomCleaner and Sayan from the cooking rotation
    const availableForCooking = members.filter(name => name !== roomCleaner && name !== 'sayan');

    // Assign Cooking: Rotate among remaining members (excluding room cleaner and Sayan)
    cook = availableForCooking[cookIndex % availableForCooking.length];
    cookIndex++;

    // Exclude roomCleaner and cook from the cooking utensils rotation
    const availableForPocha = availableForCooking.filter(name => name !== cook);

    // Assign Cooking Utensils: Rotate among remaining members
    cookingUtensils = availableForPocha[pochaIndex % availableForPocha.length];
    pochaIndex++;

    output += `📅 ${day}:\n`;
    output += `   🧼 Room Cleaning: ${roomCleaner}\n`;
    output += `   🍳 Cooking: ${cook}\n`;
    output += `   🪣 Cooking Utensils: ${cookingUtensils}\n\n`;
  });

  console.log(output);

  // Optional: If running in the browser
  if (typeof document !== 'undefined') {
    document.body.innerText = output;
  }
}

generateChoreRoutine();



